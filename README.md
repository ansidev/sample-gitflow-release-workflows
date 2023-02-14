# sample-gitflow-release-workflows

[![Release](https://img.shields.io/github/release/ansidev/sample-gitflow-release-workflows.svg)](https://github.com/ansidev/sample-gitflow-release-workflows/releases)
[![Build Status](https://github.com/ansidev/sample-gitflow-release-workflows/workflows/release/badge.svg)](https://github.com/ansidev/sample-gitflow-release-workflows/actions)

Sample Gitflow release workflow using GitHub Actions and official [GitHub CLI](https://cli.github.com/manual/).

## Features

- Auto create a draft PR on pushing new branch `release/**` or `hotfix/**`.
  - Auto add following labels for PR:
    - `automated-pr`,
    - `release-pr`: if normal release.
    - `hotfix-pr`: if hotfix release.
    - `pre-release`: if version contains `alpha`, `beta`, `rc`.
  - **Note:** You are responsible for preparing release materials: changelog, bump version,... using your favorite tools.
- Auto create and publish a new release on merging changes from `release/**` or `hotfix/**` into `main`.
- Auto create corresponding git tag with the released version.
- Auto create PR and merge changes from `release/**` or `hotfix/**` back into `develop`.

## Manual

- Workflows

  | Name                                   | Description                                     | File                                                                                                           |
  | -------------------------------------- | ----------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
  | Release                                | Automate releasing                              | [release.yaml](./.github/workflows/release.yaml)                                                               |
  | Auto merge release/hotfix into develop | Automate merging release/hotfix PR into develop | [auto_merge_release_hotfix_into_develop.yaml](./.github/workflows/auto_merge_release_hotfix_into_develop.yaml) |
  | Draft release/hotfix PR                | Automate drafting a release/hotfix PR           | [draft_release_hotfix_pr.yaml](./.github/workflows/draft_release_hotfix_pr.yaml)                               |

- You have to update below env variables if necessary

  | Environment variable | Description            | Default value |
  | -------------------- | ---------------------- | ------------- |
  | BRANCH_MAIN          | The main branch        | `main`        |
  | BRANCH_DEVELOP       | The develop branch     | `develop`     |
  | TAG_PREFIX           | The prefix for git tag | `v`           |

## Contact

Le Minh Tri [@ansidev](https://ansidev.xyz/about).

## License

This source code is available under the [MIT License](/LICENSE).
