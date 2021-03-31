# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/)
and this project adheres to [Semantic Versioning](http://semver.org/).

## [Unreleased]

## [1.0.0] - 2021-03-31

### Added

- Add `update-container-images` command to update container images of multiple deployment resources.

### Removed

- Remove `init-current-revision` and `rollback-deployment-on-fail` in favor of newly added `update-container-images` command.

## [0.0.9] - 2020-12-03

### Added

- Print information on fail. It contains events, pod description and executed manifest.

### Fixed

- Log is not output on DB migration failure.
