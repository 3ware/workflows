# 3ware reusable workflows

[![semantic-release: conventionalcommits](https://img.shields.io/badge/semantic--release-conventionalcommits-blue?logo=semantic-release)](https://github.com/semantic-release/semantic-release) [![GitHub release](https://img.shields.io/github/release/3ware/workflows?include_prereleases=&sort=semver&color=yellow)](https://github.com/3ware/workflows/releases/) [![issues - workflows](https://img.shields.io/github/issues/3ware/workflows)](https://github.com/3ware/workflows/issues) [![CI](https://github.com/3ware/workflows/actions/workflows/lint.yaml/badge.svg)](https://github.com/3ware/workflows/actions/workflows/lint.yaml)

The repository contains [GitHub Action](https://docs.github.com/en/actions) [reusable workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows) that can be consumed by other repositories.

## Table of contents

- [Workflows](#workflows)
  - [get-terraform-dir](#get-terraform-dir)
  - [lint](#lint)
  - [pr-title](#pr-title)
  - [semantic-release](#semantic-release)
  - [tfsec-pr-commenter](#tfsec-pr-commenter)

## Workflows

### get-terraform-dir

This workflow uses [changed-files](https://github.com/tj-actions/changed-files) to output the terraform working directory which can then be used by other actions to initialise terraform. This is useful for multi directory configurations.

### lint

Linting is performed using [trunk.io](https://github.com/trunk-io/trunk-action). This action makes use of the [get-terraform-dir](#get-terraform-dir) workflow, to find the terraform working directory and initialise terraform, if any terraform files have been updated, so validation and linting using [tflint](https://github.com/terraform-linters/tflint) can be performed.

### pr-title

This workflow ensures that Pull Request titles follow the [conventional syntax](https://www.conventionalcommits.org/en/v1.0.0-beta.2/) using the [semantic-pull-request](https://github.com/marketplace/actions/semantic-pull-request) action. When the Pull Request is Squashed & Merged into main, the Pull Request title is used as the commit message, which is analysed by [semantic-release](#semantic-release)

### semantic-release

[Semantic Release](https://github.com/marketplace/actions/action-for-semantic-release) generates tags and releases by mapping conventional commit messages to major, minor and patch version numbers. This action requires an authentication token to push the changes it generates to protected branches. To accomplish this, this action also incorporates [workflow-application-token-action](https://github.com/marketplace/actions/workflow-application-token-action) to generate a token using [GitHub App Authentication](https://github.com/marketplace/actions/workflow-application-token-action) for authentication.

### tfsec-pr-commenter

Terraform static code analysis is performed using [tfsec](https://github.com/aquasecurity/tfsec). This action also uses [get-terraform-dir](#get-terraform-dir) to set the working directory.
