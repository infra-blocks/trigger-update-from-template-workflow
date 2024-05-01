# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.1.1] - 2024-04-20

### Fixed

- Usage version of `check-has-semver-label`  to `check-has-semver-label@v2` in README.

## [2.1.0] - 2024-04-19

### Added

- Status badges in README.
- The `skip` input to skip on the callee's side of a `worfklow_call`. Otherwise, when the workflow is skipped from
  the caller's side (with an `if` expression), the check path when the workflow was run is not the same as when
  it was skipped ( `outer / inner` vs. `outer` when skipped) !

## [2.0.0] - 2024-01-19

### Removed

- The legacy file exporting the workflow. Now the workflow is only accessible at `.github/workflows/workflow.yml`.

## [1.1.0] - 2024-01-18

### Added

- A duplicate of the reusable workflow at the `.github/workflows/workflow.yml`. This is part of a change to have
every reusable workflow exported under the same conventional path.

## [1.0.5] - 2024-01-16

### Fixed

- Update the README to reflect the changes of [1.0.4].

## [1.0.4] - 2024-01-16

### Fixed

- Workflow permissions were not open enough. The workflow needs `pull_requests: write` permissions to
post status reports as PR comments.

## [1.0.3] - 2024-01-16

### Changed

- Update to `list-template-repository-instances@v2`

## [1.0.2] - 2024-01-15

### Changed

- Use `check-has-semver-label-workflow`
- - Updated the documentation to be more useful. Added inputs, outputs, secrets, permissions and more into the README.

### Fixed

- Example usages in the README.


## [1.0.1] - 2024-01-08

### Fixed

- Don't attempt to trigger workflow dispatch events when the repository has no instantiating repos.

## [1.0.0] - 2023-12-19

### Added

- First release!

[2.1.1]: https://github.com/infrastructure-blocks/trigger-update-from-template-workflow/compare/v2.1.0...v2.1.1
[2.1.0]: https://github.com/infrastructure-blocks/trigger-update-from-template-workflow/compare/v2.0.0...v2.1.0
[2.0.0]: https://github.com/infrastructure-blocks/trigger-update-from-template-workflow/compare/v1.1.0...v2.0.0
[1.1.0]: https://github.com/infrastructure-blocks/trigger-update-from-template-workflow/compare/v1.0.5...v1.1.0
[1.0.5]: https://github.com/infrastructure-blocks/trigger-update-from-template-workflow/compare/v1.0.4...v1.0.5
[1.0.4]: https://github.com/infrastructure-blocks/trigger-update-from-template-workflow/compare/v1.0.3...v1.0.4
[1.0.3]: https://github.com/infrastructure-blocks/trigger-update-from-template-workflow/compare/v1.0.2...v1.0.3
[1.0.2]: https://github.com/infrastructure-blocks/trigger-update-from-template-workflow/compare/v1.0.1...v1.0.2
[1.0.1]: https://github.com/infrastructure-blocks/trigger-update-from-template-workflow/compare/v1.0.0...v1.0.1
[1.0.0]: https://github.com/infrastructure-blocks/trigger-update-from-template-workflow/releases/tag/v1.0.0
