# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0] - 2021-01-18
### Added
- Clean files to keep in sync with running clusters and nodes.
- Automatically remove clusters which are not available anymore.
- Remove all resources to restart from a fresh installation.
- This change log

### Changed
- Clearly separate in help commands concerning only one cluster and all clusters.
- Remove use of temp files to compute diff between lists.

### Fixed
- Bad written test condition when dry-run used, could lead to erroneous message.
- No confirm message when checking unhealthy containers after an `apply`