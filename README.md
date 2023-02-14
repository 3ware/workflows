# 3ware reusable workflows

[![semantic-release: conventionalcommits](https://img.shields.io/badge/semantic--release-conventionalcommits-blue?logo=semantic-release)](https://github.com/semantic-release/semantic-release) [![GitHub release](https://img.shields.io/github/release/3ware/workflows?include_prereleases=&sort=semver&color=yellow)](https://github.com/3ware/workflows/releases/) [![issues - workflows](https://img.shields.io/github/issues/3ware/workflows)](https://github.com/3ware/workflows/issues) [![CI](https://github.com/3ware/workflows/actions/workflows/lint.yaml/badge.svg)](https://github.com/3ware/workflows/actions/workflows/lint.yaml)

The repository contains [GitHub Action](https://docs.github.com/en/actions) [reusable workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows) that can be consumed by other repositories.

## Table of contents

- [Workflows](#workflows)
  - [get-terraform-dir](#get-terraform-dir)
  - [get-workflow-token](#get-workflow-token)
  - [lint](#lint)
  - [pr-title](#pr-title)
  - [semantic-release](#semantic-release)
  - [tfsec-pr-commenter](#tfsec-pr-commenter)
  - [terraform-docs](#terraform-docs)

## Workflows

### get-terraform-dir

This workflow uses [changed-files](https://github.com/tj-actions/changed-files) to output the terraform working directory which can then be used by other actions to initialise terraform. This is useful for multi directory configurations.

### get-workflow-token

According to GitHubs documentation regarding [Authenticating with the API](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-authentication-to-github#authenticating-with-the-api), Personal Access Tokens (PATS) should be used temporarily for development work and production workflows should use [GitHub App Authentication](https://docs.github.com/en/developers/apps/building-github-apps/authenticating-with-github-apps). Most GitHub Action documentation for workflows that require permissions over and above what `GITHUB_TOKEN` can provide, suggest using a PAT - however I wanted to see if I could follow GitHub's advice and use an app. It can be quite easy to lose track of which PAT is stored as which action secret if you have a few of them floating around, and you don't need to worry about expiration and rotation.

This workflow uses the [workflow-application-token-action](https://github.com/marketplace/actions/workflow-application-token-action) to generate the [installation access token](https://docs.github.com/en/developers/apps/building-github-apps/authenticating-with-github-apps#authenticating-as-an-installation) using a GitHub App, which can be used in place of a Personal Access Token.

To make the workflow reusable, the output (the token), must be encrypted for use between jobs / workflows. If it isn't the runner will [skip the output](https://docs.github.com/en/actions/using-jobs/defining-outputs-for-jobs#overview) because it contains a secret, causing subsequent workflows to fail due to authentication errors.

Therefore some extra steps are required in the reusable workflow to encrypt the token and pass the output from the step to the workflow:

#### Encrypt the token output

```yaml
- name: Get GitHub authentication token
  id: get-workflow-token
  uses:
    uses: peter-murray/workflow-application-token-action@v2.1.0 # Output is 'token'

- name: Encrypt the token for reuse between jobs / workflows
  id: encrypt-token
  env:
    KEY: ${{ secrets.PGP_SECRET_SIGNING_PASSPHRASE }}
    TOKEN: ${{ steps.get-workflow-token.outputs.token }}
  run: |
    ENCRYPTED_TOKEN=$(gpg --symmetric --batch --passphrase "$KEY" \
      --output - <(echo "$TOKEN") | base64 -w0)
    echo "encrypted-token=$ENCRYPTED_TOKEN" >> $GITHUB_OUTPUT
```

#### Add Job level output

```yaml
jobs:
  get-temp-token:
    outputs:
      token: ${{ steps.encrypt-token.outputs.encrypted-token }}
```

#### Add Workflow level output

```yaml
workflow_call:
  outputs:
    temp-token:
      description: "The temporary installation access token"
      value: ${{ jobs.get-temp-token.outputs.token }}
```

The calling workflow can then access the token - but it must be decrypted before it can be used. Also remember to `::add-mask::` to prevent it being shown in the logs:

#### Use encrypted token output in calling workflow

```yaml
calling-workflow:
  needs: get-temp-token
```

#### Decrypt the token

```yaml
- name: Decrypt the installation access token
  id: decrypt-token
  env:
    KEY: ${{ secrets.PGP_SECRET_SIGNING_PASSPHRASE }}
  run: |
    DECRYPTED_TOKEN=$(gpg --decrypt --quiet --batch --passphrase "$KEY" \
    --output - <(echo "${{ needs.get-temp-token.outputs.temp-token }}" \
    | base64 --decode))
    echo "::add-mask::$DECRYPTED_TOKEN"
    echo "temp-token=$DECRYPTED_TOKEN" >> $GITHUB_OUTPUT
```

#### Use the token for authentication

```yaml
- name: Step that required token for authentication
  env:
    GITHUB_TOKEN: ${{ steps.decrypt-token.outputs.temp-token }}
```

Thanks to this [this blog post](https://nitratine.net/blog/post/how-to-pass-secrets-between-runners-in-github-actions/) and [stack overflow answer](https://stackoverflow.com/a/75387551/18073694) for the wise words. See [get-workflow-token](https://github.com/3ware/workflows/blob/main/.github/workflows/get-workflow-token.yaml) and [semantic-release](https://github.com/3ware/workflows/blob/main/.github/workflows/semantic-release.yaml) for complete workflows.

### lint

Linting is performed using [trunk.io](https://github.com/trunk-io/trunk-action). This action makes use of the [get-terraform-dir](#get-terraform-dir) workflow, to find the terraform working directory and initialise terraform, if any terraform files have been updated, so validation and linting using [tflint](https://github.com/terraform-linters/tflint) can be performed.

### pr-title

This workflow ensures that Pull Request titles follow the [conventional syntax](https://www.conventionalcommits.org/en/v1.0.0-beta.2/) using the [semantic-pull-request](https://github.com/marketplace/actions/semantic-pull-request) action. When the Pull Request is Squashed & Merged into main, the Pull Request title is used as the commit message, which is analysed by [semantic-release](#semantic-release)

### semantic-release

[Semantic Release](https://github.com/marketplace/actions/action-for-semantic-release) generates tags and releases by mapping conventional commit messages to major, minor and patch version numbers. This action requires an authentication token to push the changes it generates to protected branches. It makes use of the [get-workflow-token](#get-workflow-token) for this, instead of using a PAT.

### tfsec-pr-commenter

Terraform static code analysis is performed using [tfsec](https://github.com/aquasecurity/tfsec). This action also uses [get-terraform-dir](#get-terraform-dir) to set the working directory.

### terraform-docs

[Terraform docs](https://github.com/marketplace/actions/terraform-docs-gh-actions) generates terraform module documentation and commits the updated _README_ to the repository. This workflow uses [get-workflow-token](#get-workflow-token) for authentication and the `gh cli` for commits, as opposed to the native functionality because commits can be signed using the former. See [this gist](https://gist.github.com/swinton/03e84635b45c78353b1f71e41007fc7c).
