# Changelog

## [0.3.0](https://github.com/scalar/scalar-rs/compare/v0.2.0...v0.3.0) (2026-08-28)


### ⚠ BREAKING CHANGES

* **api:** 6 breaking changes to the SDK surface.
    - Renamed SDK from `ScalarApi` to `Scalar`.
    - Removed operation `schemas.version.retrieveSchema` (`GET /v1/schemas/{namespace}/{slug}/version/{semver}`).
    - Removed operation `schemas.version.deleteSchema` (`DELETE /v1/schemas/{namespace}/{slug}/version/{semver}`).
    - Removed operation `schemas.version.createSchema` (`POST /v1/schemas/{namespace}/{slug}/version`).
    - Removed operation `schemas.accessGroup.createSchema` (`POST /v1/schemas/{namespace}/{slug}/access-group`).
    - Removed operation `schemas.accessGroup.deleteSchema` (`DELETE /v1/schemas/{namespace}/{slug}/access-group`).

### Features

* **api:** update SDK name (+11 more changes) ([5c05476](https://github.com/scalar/scalar-rs/commit/5c054762e1582b88ddd426b2e8c7cada6fa10fd5))


### Chores

* **api:** update generated SDK content ([0ad32ff](https://github.com/scalar/scalar-rs/commit/0ad32ff331222f05ebb83b55570a081a3091a439))

## [0.2.0](https://github.com/scalar/scalar-rs/compare/v0.1.0...v0.2.0) (2026-08-07)


### Features

* **api:** initial SDK generation ([64f9473](https://github.com/scalar/scalar-rs/commit/64f94737c7e5e3536ee4b949c6ef9672a4a08f05))


### Chores

* **api:** regenerate SDK ([85534d5](https://github.com/scalar/scalar-rs/commit/85534d55f2416ac3ebf4dc9f45211ed6fd3266bd))
* **api:** regenerate SDK ([53a694a](https://github.com/scalar/scalar-rs/commit/53a694ad5e608ec2a7e80ba63d463774aab203c3))

## Changelog

All notable changes to `scalar-rs` are documented here. Release
tooling appends a section per released version below.

## Unreleased

- Initial generation of the `scalar-rs` SDK.
- Response-only models are marked `#[non_exhaustive]`, so new response
  fields can be added in future versions without a breaking release;
  request models stay literally constructible.
