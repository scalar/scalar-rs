# Changelog

## [0.4.0](https://github.com/scalar/scalar-rs/compare/v0.3.3...v0.4.0) (2026-10-02)


### ⚠ BREAKING CHANGES

* **api:** 10 breaking changes to the SDK surface.
    - Removed operation `oAuth.oauthAuthorize` (`GET /v1/oauth/authorize`).
    - Removed operation `oAuth.oauthToken` (`POST /v1/oauth/token`).
    - Removed operation `oAuth.oauthRevoke` (`POST /v1/oauth/revoke`).
    - Removed operation `oAuth.oauthAuthorizationServerMetadata` (`GET /.well-known/oauth-authorization-server`).
    - Removed schema `oauth_token`.
    - Removed schema `oauth_scope`.
    - Removed schema `oauth_error`.
    - Removed schema `oauth_token_request`.
    - Removed schema `oauth_revoke_request`.
    - Removed schema `oauth_authorization_server_metadata`.
* **api:** 4 breaking changes to the SDK surface.
    - Property `api_document.tags` type changed from `unknown` to `string`.
    - Property `managed_doc_version.tools` type changed from `Array<object>` to `Array<object>`.
    - Property `github_project.accessGroups` type changed from `unknown` to `string`.
    - Property `docs_project.accessGroups` type changed from `unknown` to `string`.
* **api:** 10 breaking changes to the SDK surface.
    - Removed body field `lastKnownVersionSha` from `registry.updateApiDocumentVersion`.
    - Removed body field `lastKnownVersionSha` from `registry.createApiDocumentVersion`.
    - Response of `schemas.version.create` changed from `uid` to `none`.
    - Schema `slug` shape changed.
    - Schema `namespace` shape changed.
    - Added required property `managed_doc_version.endpointCount`.
    - Removed optional property `managed_doc_version.versionSha`.
    - Schema `method` shape changed.
    - Added required property `github_project.userInfoHookUrl`.
    - Added required property `github_project.analyticsEnabled`.

### Features

* **api:** add operation accessGroups.create (+66 more changes) ([3e4cdd8](https://github.com/scalar/scalar-rs/commit/3e4cdd84a1e3612593bde9f0773dee3f7557dc10))
* **api:** remove operation oAuth.oauthAuthorize (+9 more changes) ([ea85807](https://github.com/scalar/scalar-rs/commit/ea85807ae77dfb1219b403cc1265e9e35d05e9a4))
* **api:** update property api_document.tags (+3 more changes) ([95d6e90](https://github.com/scalar/scalar-rs/commit/95d6e90e19d959d9968836b22efac74daaa3c835))
* **api:** update SDK surface (15 changes) ([29e170e](https://github.com/scalar/scalar-rs/commit/29e170eb751da4eb3b7b6117c5fada2b7a245bb0))


### Chores

* **api:** update generated SDK content ([be29d2c](https://github.com/scalar/scalar-rs/commit/be29d2c63745add6c2ca597948a11245ef21562e))

## [0.3.3](https://github.com/scalar/scalar-rs/compare/v0.3.2...v0.3.3) (2026-09-15)


### Chores

* **api:** update generated SDK content ([ef71c73](https://github.com/scalar/scalar-rs/commit/ef71c736bf846a9240da67030ae33ef4a698b63c))

## [0.3.2](https://github.com/scalar/scalar-rs/compare/v0.3.1...v0.3.2) (2026-09-15)


### Chores

* **api:** update generated SDK content ([e1962d2](https://github.com/scalar/scalar-rs/commit/e1962d28ae0651c5d29b91ba087a32dfc4dd7551))

## [0.3.1](https://github.com/scalar/scalar-rs/compare/v0.3.0...v0.3.1) (2026-09-15)


### Chores

* release 0.3.1 ([00c5ca7](https://github.com/scalar/scalar-rs/commit/00c5ca785b8ccacec8676a3ce4891a4903351b41))
* release 0.3.1 ([2908fac](https://github.com/scalar/scalar-rs/commit/2908fac501f3274411e8c48dd9467510fada5be1))

## [0.3.0](https://github.com/scalar/scalar-rs/compare/v0.2.0...v0.3.0) (2026-09-15)


### ⚠ BREAKING CHANGES

* **api:** Schema `timestamp` shape changed.
* **api:** 6 breaking changes to the SDK surface.
    - Renamed SDK from `ScalarApi` to `Scalar`.
    - Removed operation `schemas.version.retrieveSchema` (`GET /v1/schemas/{namespace}/{slug}/version/{semver}`).
    - Removed operation `schemas.version.deleteSchema` (`DELETE /v1/schemas/{namespace}/{slug}/version/{semver}`).
    - Removed operation `schemas.version.createSchema` (`POST /v1/schemas/{namespace}/{slug}/version`).
    - Removed operation `schemas.accessGroup.createSchema` (`POST /v1/schemas/{namespace}/{slug}/access-group`).
    - Removed operation `schemas.accessGroup.deleteSchema` (`DELETE /v1/schemas/{namespace}/{slug}/access-group`).

### Features

* **api:** update schema timestamp (+1 more change) ([0f864c8](https://github.com/scalar/scalar-rs/commit/0f864c88b412123c7e38494a94c3f7464a0b0c42))
* **api:** update SDK name (+11 more changes) ([5c05476](https://github.com/scalar/scalar-rs/commit/5c054762e1582b88ddd426b2e8c7cada6fa10fd5))


### Chores

* **api:** regenerate SDK ([f4e82a9](https://github.com/scalar/scalar-rs/commit/f4e82a9c3a669dec3cbdf57f9351e1b35c6de958))
* **api:** regenerate SDK ([c6d7d9c](https://github.com/scalar/scalar-rs/commit/c6d7d9cbd0f847040062864fd5fb48c16d8f98c4))
* **api:** update generated SDK content ([eaabbf2](https://github.com/scalar/scalar-rs/commit/eaabbf290211e9117905cdd108658dd3f17eae7e))
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
