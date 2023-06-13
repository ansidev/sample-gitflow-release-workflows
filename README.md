# sample-gitflow-release-workflows

[![Release](https://img.shields.io/github/release/ansidev/sample-gitflow-release-workflows.svg)](https://github.com/ansidev/sample-gitflow-release-workflows/releases)
[![Build Status](https://github.com/ansidev/sample-gitflow-release-workflows/workflows/release/badge.svg)](https://github.com/ansidev/sample-gitflow-release-workflows/actions)

Sample Gitflow release workflow using GitHub Actions and official [GitHub CLI](https://cli.github.com/manual/).

Since [v1.1.4](https://github.com/ansidev/sample-gitflow-release-workflows/releases/tag/v1.1.4), I created [Gitflow GitHub Actions](https://github.com/ghacts/gitflow) for reusing and applied them in this repository.

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

  | Name                              | Description                                  | File                                                                                 |
  | --------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------------ |
  | Create release PR                 | Automate creating a release/hotfix PR        | [create_release_pr.yml](./.github/workflows/create_release_pr.yml)                   |
  | Publish release                   | Automate publishing new release              | [publish_release.yml](./.github/workflows/publish_release.yml)                       |
  | Merge release/hotfix into develop | Automate merging release/hotfix into develop | [merge_release_into_develop.yml](./.github/workflows/merge_release_into_develop.yml) |

- You have to update below env variables if necessary

  | Environment variable | Description            | Default value |
  | -------------------- | ---------------------- | ------------- |
  | TAG_PREFIX           | The prefix for git tag | `v`           |

  **Note**: If you don't use the above default values, you have to update corresponding values for the workflow(s).

## Reference documentations

- [Events that trigger workflows](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows).
- [Webhook events and payloads](https://docs.github.com/developers/webhooks-and-events/webhooks/webhook-events-and-payloads).

## Contact

Le Minh Tri [@ansidev](https://ansidev.xyz/about).

## License

This source code is available under the [MIT License](/LICENSE).
