# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.0] - 2026-09-12

### Added

- Repository governance: README, contributing guide, security policy, code of conduct, MIT license.
- CI: toolchain check, commit lint, and secret scanning workflows.
- Pinned Node version and repository configuration.

### Fixed

- Secret scanning runs the pinned gitleaks binary directly, which works on organization repositories without a license key.

[Unreleased]: https://github.com/Mvua-Protocol/mvua-app/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/Mvua-Protocol/mvua-app/releases/tag/v0.1.0
