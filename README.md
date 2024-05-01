# trigger-update-from-template-workflow
[![Release](https://github.com/infrastructure-blocks/trigger-update-from-template-workflow/actions/workflows/release.yml/badge.svg)](https://github.com/infrastructure-blocks/trigger-update-from-template-workflow/actions/workflows/release.yml)
[![Update From Template](https://github.com/infrastructure-blocks/trigger-update-from-template-workflow/actions/workflows/update-from-template.yml/badge.svg)](https://github.com/infrastructure-blocks/trigger-update-from-template-workflow/actions/workflows/update-from-template.yml)

Reusable workflow to use on a template repository to trigger the
[merge-template-workflow](https://github.com/infrastructure-blocks/merge-template-workflow)
on all repositories of the same organization that instantiate the template (calling this workflow).

## Inputs

|   Name   | Required | Description                                                                                                                                                                  |
|:--------:|:--------:|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   skip   |  false   | A boolean indicating whether to skip the workflow. This is to workaround the required checks discrepancy when the workflow is skipped from the caller. It defaults to false. |
| workflow |  false   | The workflow file being trigger with a workflow dispatch event. Defaults to "update-from-template.yml".                                                                      |


## Secrets

|    Name    | Required | Description                                                                                                          |
|:----------:|:--------:|----------------------------------------------------------------------------------------------------------------------|
| github-pat |   true   | The personal access token used to authenticate for certain operations that cannot be achieved with the GitHub Token. |

## Outputs

N/A

## Permissions

|     Scope     | Level | Reason                                 |
|:-------------:|:-----:|----------------------------------------|
| pull-requests | write | To post status reports as PR comments. |

## Concurrency controls

|      Field         |                 Value                    |
|:------------------:|:----------------------------------------:|
|       group        | ${{ github.workflow }}-${{ github.ref }} |
| cancel-in-progress |                   true                   | 

## Timeouts

N/A

## Usage

```yaml
name: Trigger Update From Template

# We do it on pull request "merge" event so we can get the label and propagate it more easily.
on:
  pull_request:
    branches:
      - master
    types:
      - closed

permissions:
  pull-requests: write

jobs:
  trigger-update-from-template:
    uses: infrastructure-blocks/trigger-update-from-template-workflow/.github/workflows/workflow.yml@v1
    secrets:
      github-pat: ${{ secrets.PAT }}
```

### Releasing

The releasing is handled at git level with semantic versioning tags. Those are automatically generated and managed
by the [git-tag-semver-from-label-workflow](https://github.com/infrastructure-blocks/git-tag-semver-from-label-workflow).
