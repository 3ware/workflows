# 3ware reusable workflows

[![GitHub release](https://img.shields.io/github/release/3ware/workflows?include_prereleases=&sort=semver&color=green)](https://github.com/3ware/workflows/releases/) [![issues - workflows](https://img.shields.io/github/issues/3ware/workflows)](https://github.com/3ware/workflows/issues) [![CI](https://img.shields.io/github/actions/workflow/status/3ware/workflows/pr-check.yaml?label=CI&logo=githubactions&logoColor=white)](https://github.com/3ware/workflows/actions/workflows/pr-check.yaml)

Contains [GitHub Action](https://docs.github.com/en/actions) [reusable workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows) and [composite actions](https://docs.github.com/en/actions/tutorials/create-actions/create-a-composite-action) that can be consumed by other repositories.

<details>
<summary><strong>Table of contents</strong></summary>

- [3ware reusable workflows](#3ware-reusable-workflows)
  - [Reusable Workflows](#reusable-workflows)
    - [Pull Request Title Validation](#pull-request-title-validation)
      - [Inputs](#inputs)
      - [Secrets](#secrets)
      - [Permissions](#permissions)
    - [Trunk Code Quality](#trunk-code-quality)
      - [Inputs](#inputs-1)
      - [Secrets](#secrets-1)
      - [Permissions](#permissions-1)
  - [Composite Actions](#composite-actions)
    - [Trunk tofu init](#trunk-tofu-init)
      - [Inputs](#inputs-2)
      - [Recommended Folder Structure](#recommended-folder-structure)

</details>

## Reusable Workflows

### Pull Request Title Validation

Validate the pull request title conforms to the [conventional commit specification](https://www.conventionalcommits.org/en/v1.0.0/). This is important because all changes must be made through pull requests. Commits are _squashed_ when the pull request is merged and the pull request title is used as the commit message. Accurate release notes and version tags can be generated when commits follow the spec.

#### Inputs

- `scopes` (optional) Newline delimited list of commit scopes. Defaults to empty.

#### Secrets

GitHub App, with `contents:write` permission, required to trigger a check run when an incorrect pull request title is corrected.

- `github-app-id` (required)
- `github-app-private-key` (required)

#### Permissions

- `contents: read`
- `pull-requests: write`

> [!WARNING]
> Do not define a workflow-level concurrency group in the calling workflow. The reusable workflow already defines a job-level group per pull request.

```yaml
name: Example PR Workflow

on:
  pull_request:
    types: [opened, edited, reopened, synchronize]
    branches: [main]

permissions: {}

jobs:
  validate-pr-title:
    name: Validate PR Title
    permissions:
      contents: read
      pull-requests: write
    uses: 3ware/workflows/.github/workflows/reusable-validate-pr-title.yaml@v5.0.0
    with:
      scopes: |
        build
        deps
    secrets:
      github-app-id: ${{ secrets.GH_APP_ID }}
      github-app-private-key: ${{ secrets.GH_APP_PRIVATE_KEY }}
```

### Trunk Code Quality

Runs [trunk code quality](https://docs.trunk.io/code-quality/overview), configured via the `.trunk/trunk.yaml` configuration file, on changes made via pull requests.

#### Inputs

- `persist-credentials` (optional). Defaults to `false`.
- `owner` (optional). Owner the GitHub App token is scoped to. Defaults to the calling repository's owner.
- `additional-repos` (optional). Newline delimited repository names, in addition to the calling repository, the token is scoped to. Defaults to `workflows`.

#### Secrets

GitHub App, which creates an organisation token for specific repositories, that allows `zizmor` to run in [online mode](https://docs.zizmor.sh/usage/#operating-modes).

- `github-app-id` (required)
- `github-app-private-key` (required)

#### Permissions

- `contents: read`

> [!WARNING]
> Do not define a workflow-level concurrency group in the calling workflow. The reusable workflow already cancels superseded runs on the same pull request; a matching caller group can cause the run to be cancelled as a deadlock.

```yaml
name: Example Lint Workflow

on:
  pull_request:
    types: [opened, reopened, synchronize]
    branches: [main]

# Disable permissions for all available scopes
permissions: {}

jobs:
  trunk:
    name: Trunk Code Quality
    permissions:
      contents: read
    uses: 3ware/workflows/.github/workflows/reusable-trunk-code-quality.yaml@v5.0.0
    secrets:
      github-app-id: ${{ secrets.GH_APP_ID }}
      github-app-private-key: ${{ secrets.GH_APP_PRIVATE_KEY }}
```

---

## Composite Actions

### Trunk tofu init

Trunk's action uses a composite action defined in [setup-ci](https://github.com/trunk-io/trunk-action#custom-setup) to prepare a workspace if necessary before any linters are run. Trunk is used to `fmt`, `validate` and `tflint` Infrastructure-as-Code projects. These tools require the IaC directory to be initialised with `tofu init`. The purpose of `trunk-tofu-init` is to detect file modification within IaC directories and initialise them prior to running `trunk check`.

When the `IS_TRUNK_UPGRADE` or `INIT_ALL_MODULES` environment variable is `true`, every directory containing `.tf` files is initialised instead of only the changed ones.

#### Inputs

- `tofu-version` (required)
- `dir-max-depth` (optional, default `3`)
- `iac-dir-path` (optional, default `iac`)

Define the following workflow in `.trunk/setup-ci/action.yaml`:

```yaml
name: Trunk Code Quality Setup
description: Set up dependencies for Trunk Code Quality

runs:
  using: composite
  steps:
    - name: Initialise OpenTofu Directories
      uses: 3ware/workflows/.github/actions/trunk-tofu-init@v5.0.0
      with:
        tofu-version: 1.13.0
```

> [!TIP]
> For ease of configuration follow the recommended IaC project folder structure below

#### Recommended Folder Structure

```txt
iac
├── environments
└── modules
    ├── module1
    └── module2
```
