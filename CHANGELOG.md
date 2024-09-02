# Changelog

All notable changes to this project will be documented in this file.

## [4.1.0](https://github.com/3ware/workflows/compare/v4.0.0...v4.1.0) (2024-09-02)


### Enhancement

* **terraform-docs:** Use native `find-dir` functionality and 3ware-release token ([#106](https://github.com/3ware/workflows/issues/106)) ([25be5ab](https://github.com/3ware/workflows/commit/25be5abccffcbcd96e60cab728f4444c8d960aee))

## [4.0.0](https://github.com/3ware/workflows/compare/v3.2.0...v4.0.0) (2024-08-31)


### ⚠ BREAKING CHANGES

* Remove `contents: read` workflow permission (#105)

### Features

* Remove `contents: read` workflow permission ([#105](https://github.com/3ware/workflows/issues/105)) ([2b772d3](https://github.com/3ware/workflows/commit/2b772d3c2dcad87077f2ffc14b43de8e24a701f4))

## [3.2.0](https://github.com/3ware/workflows/compare/v3.1.3...v3.2.0) (2024-08-30)


### Enhancement

* **terraform-docs:** Summaries and references ([#104](https://github.com/3ware/workflows/issues/104)) ([5e07a3b](https://github.com/3ware/workflows/commit/5e07a3b94d3dbf898036dd77fcc9b906adbb1863))

## [3.1.3](https://github.com/3ware/workflows/compare/v3.1.2...v3.1.3) (2024-08-30)


### Bug Fixes

* **get-terraform-dir:** Resolve incorrect job summary step being run ([#103](https://github.com/3ware/workflows/issues/103)) ([f261ac4](https://github.com/3ware/workflows/commit/f261ac42450b5bf0cec7cef45acb8efd38a3e6db))

## [3.1.2](https://github.com/3ware/workflows/compare/v3.1.1...v3.1.2) (2024-08-29)


### Bug Fixes

* **get-terraform-dir:** Resolve error when multiple directories returned ([#102](https://github.com/3ware/workflows/issues/102)) ([b0ed4ae](https://github.com/3ware/workflows/commit/b0ed4ae8b62061bdea3058b2ca1e7a4613405ec9))

## [3.1.1](https://github.com/3ware/workflows/compare/v3.1.0...v3.1.1) (2024-08-29)


### Bug Fixes

* **lint:** Write the terraform version to an environment variable ([#100](https://github.com/3ware/workflows/issues/100)) ([206c279](https://github.com/3ware/workflows/commit/206c279ba8190b1d2c277bab58903cf326b40f04))

## [3.1.0](https://github.com/3ware/workflows/compare/v3.0.1...v3.1.0) (2024-08-28)


### Features

* **get-workflow-token:** Add condition to check the GitHub repository owner ([#99](https://github.com/3ware/workflows/issues/99)) ([7450cd6](https://github.com/3ware/workflows/commit/7450cd68c5857aa281b43fbc950d0a28b26e3c98))

## [3.0.1](https://github.com/3ware/workflows/compare/v3.0.0...v3.0.1) (2024-08-28)


### Bug Fixes

* **release:** Checkout step authentication ([#97](https://github.com/3ware/workflows/issues/97)) ([dfe4a62](https://github.com/3ware/workflows/commit/dfe4a62274f759e167efb1e055a6aa338e94e9ff))

## [3.0.0](https://github.com/3ware/workflows/compare/v2.6.0...v3.0.0) (2024-08-27)


### ⚠ BREAKING CHANGES

* **release:** Remove `contents: read` permissions (#95)

### Features

* **release:** Remove `contents: read` permissions ([#95](https://github.com/3ware/workflows/issues/95)) ([10aa9ec](https://github.com/3ware/workflows/commit/10aa9ec56dd2ba84d1871c4bc5732953d3cbcce0))

## [2.6.0](https://github.com/3ware/workflows/compare/v2.5.0...v2.6.0) (2024-08-23)


### Enhancement

* **lint:** Terraform / Tofu  changes ([#93](https://github.com/3ware/workflows/issues/93)) ([bfff713](https://github.com/3ware/workflows/commit/bfff7133bd44623dd376b00a819d6c624248ec02))

## [2.5.0](https://github.com/3ware/workflows/compare/v2.4.0...v2.5.0) (2024-04-08)


### Features

* **pr-title:** Add job summary and PR comments ([#91](https://github.com/3ware/workflows/issues/91)) ([7f2488f](https://github.com/3ware/workflows/commit/7f2488fa06ddb351518e386fd69dcc7a68dc9178))

## [2.4.0](https://github.com/3ware/workflows/compare/v2.3.0...v2.4.0) (2024-03-28)


### Features

* **release:** Add job summaries ([#89](https://github.com/3ware/workflows/issues/89)) ([5ca3d6b](https://github.com/3ware/workflows/commit/5ca3d6b8954a06e6636ec6cf5d19b2f6de2084be))

## [2.3.0](https://github.com/3ware/workflows/compare/v2.2.0...v2.3.0) (2024-03-28)


### Enhancement

* **terraform-docs:** Upgrade and improvements ([#87](https://github.com/3ware/workflows/issues/87)) ([5df4a0f](https://github.com/3ware/workflows/commit/5df4a0f26bfedff1d69720ddd42dc8cc6b9e8ae8))

## [2.2.0](https://github.com/3ware/workflows/compare/v2.1.0...v2.2.0) (2024-03-26)


### Features

* **get-terraform-dir:** Improve job summaries ([#84](https://github.com/3ware/workflows/issues/84)) ([4189af8](https://github.com/3ware/workflows/commit/4189af8d0654ffc9ea7e7a404698e1eb6cd88ae2))
* **terraform-docs:** Upgrade to v1.1.0 ([#85](https://github.com/3ware/workflows/issues/85)) ([d3fe3fe](https://github.com/3ware/workflows/commit/d3fe3fe0504425f4dd860349eda38275324aa905))

## [2.1.0](https://github.com/3ware/workflows/compare/v2.0.1...v2.1.0) (2024-03-26)


### Enhancement

* **lint:** Replace setup terraform with setup opentofu ([#83](https://github.com/3ware/workflows/issues/83)) ([c7bafd6](https://github.com/3ware/workflows/commit/c7bafd6d1e7f2b2a1cf6dd6a1cdbe9503888bf7c))

## [2.0.1](https://github.com/3ware/workflows/compare/v2.0.0...v2.0.1) (2024-02-21)


### Bug Fixes

* **terraform-docs:** Remove `head_ref` from relevent jobs ([#80](https://github.com/3ware/workflows/issues/80)) ([dcd1b28](https://github.com/3ware/workflows/commit/dcd1b28273683662ba6da21bf77a848264a1e121))

## [2.0.0](https://github.com/3ware/workflows/compare/v1.13.0...v2.0.0) (2024-02-14)


### ⚠ BREAKING CHANGES

* **terraform-docs:** Add required input for `terraform-dir` (#78)

### Enhancement

* **terraform-docs:** Add required input for `terraform-dir` ([#78](https://github.com/3ware/workflows/issues/78)) ([bb05220](https://github.com/3ware/workflows/commit/bb052200a37f54caebc01c9e07d993a2523fce0f))

## [1.13.0](https://github.com/3ware/workflows/compare/v1.12.0...v1.13.0) (2024-01-31)


### Features

* Create delete-workflow-run action ([#77](https://github.com/3ware/workflows/issues/77)) ([aaaefb2](https://github.com/3ware/workflows/commit/aaaefb267f06a73dfd2a44a469354e756fbc3766))

## [1.12.0](https://github.com/3ware/workflows/compare/v1.11.0...v1.12.0) (2024-01-31)


### Bug Fixes

* workflow secrets ([#76](https://github.com/3ware/workflows/issues/76)) ([6af0241](https://github.com/3ware/workflows/commit/6af0241fdfa835151b641160196e0966fe3e556a))


### Enhancement

* Workflow file updates ([#75](https://github.com/3ware/workflows/issues/75)) ([6404f02](https://github.com/3ware/workflows/commit/6404f02ac4801e08a4c8c0aab608e61a69abb93d))

## [1.11.0](https://github.com/3ware/workflows/compare/v1.10.0...v1.11.0) (2024-01-31)


### ⚠ BREAKING CHANGES

* Update workflows to accept multiple terraform directories (#74)

### Enhancement

* Update workflows to accept multiple terraform directories ([#74](https://github.com/3ware/workflows/issues/74)) ([f4fdf57](https://github.com/3ware/workflows/commit/f4fdf57f1177ddf17d73134a8957dacaa73f3328))

## [1.10.0](https://github.com/3ware/workflows/compare/v1.9.18...v1.10.0) (2023-11-24)


### Features

* 72-tfswitch ([#73](https://github.com/3ware/workflows/issues/73)) ([9262dff](https://github.com/3ware/workflows/commit/9262dff00c203fa4c19788be2d2e745c34f81795))

## [1.9.18](https://github.com/3ware/workflows/compare/v1.9.17...v1.9.18) (2023-11-23)


### Bug Fixes

* lint workflow secrets ([#70](https://github.com/3ware/workflows/issues/70)) ([8651cc4](https://github.com/3ware/workflows/commit/8651cc4bade3786d4cdaa0969e075bf2e03de717))

## [1.9.17](https://github.com/3ware/workflows/compare/v1.9.16...v1.9.17) (2023-11-23)


### Chores

* **deps:** bump actions/dependency-review-action from 3.0.3 to 3.0.6 ([#67](https://github.com/3ware/workflows/issues/67)) ([07f858f](https://github.com/3ware/workflows/commit/07f858f9e3d8a091018eba8eea7f5c6623da7dae))

## [1.9.16](https://github.com/3ware/workflows/compare/v1.9.15...v1.9.16) (2023-11-23)


### Chores

* **deps:** bump trunk-io/trunk-action from 1.0.7 to 1.1.1 ([#66](https://github.com/3ware/workflows/issues/66)) ([8301bf7](https://github.com/3ware/workflows/commit/8301bf7411fa49f6c0b5c16a05aa583870c07edf))

## [1.9.15](https://github.com/3ware/workflows/compare/v1.9.14...v1.9.15) (2023-11-23)


### Chores

* **deps:** bump actions/checkout from 3.3.0 to 3.5.2 ([#64](https://github.com/3ware/workflows/issues/64)) ([eb4640f](https://github.com/3ware/workflows/commit/eb4640f943bcf4920c103f86f6be07d6b26343c4))

## [1.9.14](https://github.com/3ware/workflows/compare/v1.9.13...v1.9.14) (2023-11-23)


### Chores

* **deps:** bump amannn/action-semantic-pull-request from 5.1.0 to 5.2.0 ([#63](https://github.com/3ware/workflows/issues/63)) ([2e583d1](https://github.com/3ware/workflows/commit/2e583d1d295dcd9ebf28fbb9c1a560cf496b8a17))

## [1.9.13](https://github.com/3ware/workflows/compare/v1.9.12...v1.9.13) (2023-03-17)


### Bug Fixes

* workflow token permissions ([#58](https://github.com/3ware/workflows/issues/58)) ([10a468f](https://github.com/3ware/workflows/commit/10a468f6e61f60e693166021d4f3ce9bddea71ab))

## [1.9.12](https://github.com/3ware/workflows/compare/v1.9.11...v1.9.12) (2023-03-16)


### Bug Fixes

* tfsec top level workflow permissions ([#57](https://github.com/3ware/workflows/issues/57)) ([0c851b5](https://github.com/3ware/workflows/commit/0c851b51131f58b211ae0441935b0700a1cadd0d))

## [1.9.11](https://github.com/3ware/workflows/compare/v1.9.10...v1.9.11) (2023-03-16)


### Bug Fixes

* pin get-terraform-dir workflow to sha ([#56](https://github.com/3ware/workflows/issues/56)) ([9020d81](https://github.com/3ware/workflows/commit/9020d81a7abc2d60e52d51c8ec7b4499baebd4b4))

## [1.9.10](https://github.com/3ware/workflows/compare/v1.9.9...v1.9.10) (2023-03-16)


### Bug Fixes

* workflow permissions ([#54](https://github.com/3ware/workflows/issues/54)) ([af1c78e](https://github.com/3ware/workflows/commit/af1c78e8d2531a9561d96058e4ebfed6289e361a))

## [1.9.9](https://github.com/3ware/workflows/compare/v1.9.8...v1.9.9) (2023-03-07)


### Chores

* **deps:** bump actions/dependency-review-action from 2.5.1 to 3.0.3 ([#51](https://github.com/3ware/workflows/issues/51)) ([14d2a90](https://github.com/3ware/workflows/commit/14d2a90b56dd1dfa10361b1e258d9d7be462a0e6))

## [1.9.8](https://github.com/3ware/workflows/compare/v1.9.7...v1.9.8) (2023-03-07)


### Chores

* **deps:** bump actions/upload-artifact from 3.1.0 to 3.1.2 ([#49](https://github.com/3ware/workflows/issues/49)) ([a115c66](https://github.com/3ware/workflows/commit/a115c6672006a3cb904c5a8874fb5471f8306268))

## [1.9.7](https://github.com/3ware/workflows/compare/v1.9.6...v1.9.7) (2023-03-06)


### Chores

* **deps:** bump github/codeql-action from 2.2.4 to 2.2.5 ([#48](https://github.com/3ware/workflows/issues/48)) ([2461b47](https://github.com/3ware/workflows/commit/2461b47ad4f1fbd14f0435321e555f376b217e29))

## [1.9.6](https://github.com/3ware/workflows/compare/v1.9.5...v1.9.6) (2023-03-03)


### Chores

* **deps:** bump trunk-io/trunk-action from 1.0.6 to 1.0.7 ([#47](https://github.com/3ware/workflows/issues/47)) ([5c289e3](https://github.com/3ware/workflows/commit/5c289e3b800b1fc650b2d721d27188d6add51824))

## [1.9.5](https://github.com/3ware/workflows/compare/v1.9.4...v1.9.5) (2023-03-03)


### Bug Fixes

* Add synchronize pull request type ([7f2d0f9](https://github.com/3ware/workflows/commit/7f2d0f9439f4a9d1ba575d22b23836bcf86d2cef))

## [1.9.4](https://github.com/3ware/workflows/compare/v1.9.3...v1.9.4) (2023-03-03)


### Bug Fixes

* workflow concurrency groups ([#53](https://github.com/3ware/workflows/issues/53)) ([48fa9a1](https://github.com/3ware/workflows/commit/48fa9a1f298abbc27eaa0cba237d81027e1e391b))


### Chores

* **deps:** bump tj-actions/changed-files from 35.5.6 to 35.6.1 ([#50](https://github.com/3ware/workflows/issues/50)) ([786e63a](https://github.com/3ware/workflows/commit/786e63acb1482f7ce92f412e53a98e2851f17562))

## [1.9.3](https://github.com/3ware/workflows/compare/v1.9.2...v1.9.3) (2023-02-25)


### Bug Fixes

* pin workflow dependencies to hash ([#45](https://github.com/3ware/workflows/issues/45)) ([e62a20b](https://github.com/3ware/workflows/commit/e62a20bd57926694764d3af20a81d6c5ebf4b424))

## [1.9.2](https://github.com/3ware/workflows/compare/v1.9.1...v1.9.2) (2023-02-24)


### Bug Fixes

* lint workflow token permissions ([#44](https://github.com/3ware/workflows/issues/44)) ([38ed872](https://github.com/3ware/workflows/commit/38ed8721102a8189da39bda062f080dce4bc5f39)), closes [#43](https://github.com/3ware/workflows/issues/43)

## [1.9.1](https://github.com/3ware/workflows/compare/v1.9.0...v1.9.1) (2023-02-24)


### Bug Fixes

* Add top level read only permissions ([#42](https://github.com/3ware/workflows/issues/42)) ([1521340](https://github.com/3ware/workflows/commit/15213404667661fd6b16c0a39e2660e6c6f09197)), closes [#41](https://github.com/3ware/workflows/issues/41)

## [1.9.0](https://github.com/3ware/workflows/compare/v1.8.0...v1.9.0) (2023-02-24)


### Features

* add ossf workflow ([#40](https://github.com/3ware/workflows/issues/40)) ([f443462](https://github.com/3ware/workflows/commit/f443462946b2386c48b4c6b5aee3db6077ca8c08)), closes [#23](https://github.com/3ware/workflows/issues/23)

## [1.8.0](https://github.com/3ware/workflows/compare/v1.7.2...v1.8.0) (2023-02-20)


### Enhancement

* update references to new secret names ([#39](https://github.com/3ware/workflows/issues/39)) ([d8cfa70](https://github.com/3ware/workflows/commit/d8cfa7072778e5271c49030a2945278861a69712))
* Update workflow secret references ([#37](https://github.com/3ware/workflows/issues/37)) ([b4df8b7](https://github.com/3ware/workflows/commit/b4df8b7ee53802c4553b936382a7f19d5957a240))

## [1.7.2](https://github.com/3ware/workflows/compare/v1.7.1...v1.7.2) (2023-02-20)


### Bug Fixes

* Remove hcl files from terraform-docs ([#36](https://github.com/3ware/workflows/issues/36)) ([287fafa](https://github.com/3ware/workflows/commit/287fafa6a5f45aa6a2738a2cf6a2be60b3ac9159))

## [1.7.1](https://github.com/3ware/workflows/compare/v1.7.0...v1.7.1) (2023-02-17)


### Bug Fixes

* terraform-docs job summary syntax ([4da90f1](https://github.com/3ware/workflows/commit/4da90f1e94cf0754bba07c4e31c26e1dd0f98e10))

## [1.7.0](https://github.com/3ware/workflows/compare/v1.6.0...v1.7.0) (2023-02-16)


### Features

* workflow improvements and fixes ([#34](https://github.com/3ware/workflows/issues/34)) ([2987d37](https://github.com/3ware/workflows/commit/2987d3713fd10ff96222fb94c63811ed1c1a82e9)), closes [#30](https://github.com/3ware/workflows/issues/30)


### Bug Fixes

* change workflow concurrency level  ([#35](https://github.com/3ware/workflows/issues/35)) ([0cef516](https://github.com/3ware/workflows/commit/0cef516f96c08e3b604a0a50d7266158458a5d40))

## [1.6.0](https://github.com/3ware/workflows/compare/v1.5.0...v1.6.0) (2023-02-16)


### Enhancement

* terraform-docs workflow ([#29](https://github.com/3ware/workflows/issues/29)) ([572b0ce](https://github.com/3ware/workflows/commit/572b0ce66399d590676b5725c12cb2ab21e77878)), closes [#28](https://github.com/3ware/workflows/issues/28)

## [1.5.0](https://github.com/3ware/workflows/compare/v1.4.0...v1.5.0) (2023-02-14)


### Enhancement

* semantic-release action to use get-temp-token ([#25](https://github.com/3ware/workflows/issues/25)) ([aacf707](https://github.com/3ware/workflows/commit/aacf707f0c29251e25e7fe4e3c8b58db3bcfb747))

## [1.4.0](https://github.com/3ware/workflows/compare/v1.3.0...v1.4.0) (2023-02-13)


### Features

* Add step to push signed commits in terraform-docs ([#24](https://github.com/3ware/workflows/issues/24)) ([b401a8f](https://github.com/3ware/workflows/commit/b401a8f947ef8a4fe8e537397dbcf759c787844d)), closes [#22](https://github.com/3ware/workflows/issues/22)

## [1.3.0](https://github.com/3ware/workflows/compare/v1.2.0...v1.3.0) (2023-02-11)


### Features

* Add reusable workflow for terraform-docs ([#20](https://github.com/3ware/workflows/issues/20)) ([488f7f0](https://github.com/3ware/workflows/commit/488f7f0b481de752564e16bf67e6936757eae594))

## [1.2.0](https://github.com/3ware/workflows/compare/v1.1.0...v1.2.0) (2023-02-09)


### Features

* tfsec action inputs ([#15](https://github.com/3ware/workflows/issues/15)) ([678ac31](https://github.com/3ware/workflows/commit/678ac31a5e67c4100aaa11cfc62f2407db7bca0a))

## [1.1.0](https://github.com/3ware/workflows/compare/v1.0.3...v1.1.0) (2023-02-07)


### Features

* Add workflow for changed files ([#16](https://github.com/3ware/workflows/issues/16)) ([b58334a](https://github.com/3ware/workflows/commit/b58334aba44e21dff28a2768d5d1b470c4aa9bcf))

## [1.0.3](https://github.com/3ware/workflows/compare/v1.0.2...v1.0.3) (2023-02-02)


### Chores

* **deps:** bump trunk-io/trunk-action from 1.0.4 to 1.0.6 ([#12](https://github.com/3ware/workflows/issues/12)) ([7bffa84](https://github.com/3ware/workflows/commit/7bffa84312a0e5da4930678e0cdd3335e7290942))

## [1.0.2](https://github.com/3ware/workflows/compare/v1.0.1...v1.0.2) (2023-02-02)


### Chores

* **deps:** bump amannn/action-semantic-pull-request from 4 to 5 ([#7](https://github.com/3ware/workflows/issues/7)) ([3958e45](https://github.com/3ware/workflows/commit/3958e45e3ea7015553a233b101611b924d8a2183))
* **deps:** bump aquasecurity/tfsec-pr-commenter-action from 1.2.0 to 1.3.1 ([#9](https://github.com/3ware/workflows/issues/9)) ([4f17bf3](https://github.com/3ware/workflows/commit/4f17bf3940a74622a94318a0b25943c8833389dd))

### [1.0.1](https://github.com/3ware/terraform-template/compare/v1.0.0...v1.0.1) (2022-09-27)


### Bug Fixes

* **terraform:** Add default value to pr reviewer count attribute ([66d7943](https://github.com/3ware/terraform-template/commit/66d7943c005990de035c3be75ff3153dcd1a5a55))

## 1.0.0 (2022-07-24)


### Features

* **repo:** Add workflow and associated configuration files ([#1](https://github.com/3ware/terraform-template/issues/1)) ([d6fa36a](https://github.com/3ware/terraform-template/commit/d6fa36abe604d2095a3d2b8bc0f3e72bc310b8da))
