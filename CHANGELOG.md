# Changelog

## [0.6.0](https://github.com/scalar/scalar-rs/compare/v0.5.0...v0.6.0) (2026-11-26)


### ⚠ BREAKING CHANGES

* **api:** 2 breaking changes to the SDK surface.
    - fields models::ScalarDocsPublishProjectBody.commit_sha — field retyped (breaking: changed in a way existing callers can observe)
    - params models::ScalarDocsPublishProjectBody.with_commit_sha/#0 — argument value retyped (breaking: changed in a way existing callers can observe)

### Features

* **api:** update SDK surface (4 changes) ([9826aad](https://github.com/scalar/scalar-rs/commit/9826aada642354d6fef4e53c48814a1888b1f56f))

## [0.5.0](https://github.com/scalar/scalar-rs/compare/v0.4.0...v0.5.0) (2026-11-25)


### ⚠ BREAKING CHANGES

* **api:** 2 breaking changes to the SDK surface.
    - fields models::SdksCreateBody.languages — field retyped (breaking: changed in a way existing callers can observe)
    - params models::SdksCreateBody.new/#1 — argument languages only in before (breaking: the new snapshot no longer has it)
* **api:** 37 breaking changes to the SDK surface.
    - types InstallationsCreateAccessGroupBody — reexport only in before (breaking: removed; McpServerListItemEnvironment, McpServerListItem appeared in its place, likely a rename)
    - types InstallationsDeleteAccessGroupBody — reexport only in before (breaking: removed; McpServerListItemEnvironment, McpServerListItem appeared in its place, likely a rename)
    - types InstallationsUpdateBody — reexport only in before (breaking: removed; McpServerListItemEnvironment, McpServerListItem appeared in its place, likely a rename)
    - types McpInstallation — reexport only in before (breaking: removed; McpServerListItem, McpServerListItemEnvironment appeared in its place, likely a rename)
    - types McpInstallationListItem — reexport only in before (breaking: removed; McpServerListItem, McpServerListItemEnvironment appeared in its place, likely a rename)
    - types ServersUpdateBody — reexport only in before (breaking: removed; McpServerListItem, McpServerListItemEnvironment appeared in its place, likely a rename)
    - types models::InstallationsCreateAccessGroupBody — struct only in before (breaking: removed; McpServerListItemEnvironment, McpServerListItem appeared in its place, likely a rename)
    - types models::InstallationsDeleteAccessGroupBody — struct only in before (breaking: removed; McpServerListItemEnvironment, McpServerListItem appeared in its place, likely a rename)
    - types models::InstallationsUpdateBody — struct only in before (breaking: removed; McpServerListItemEnvironment, McpServerListItem appeared in its place, likely a rename)
    - types models::McpInstallation — struct only in before (breaking: removed; McpServerListItem, McpServerListItemEnvironment appeared in its place, likely a rename)
    - types models::McpInstallationListItem — struct only in before (breaking: removed; McpServerListItem, McpServerListItemEnvironment appeared in its place, likely a rename)
    - types models::ServersUpdateBody — struct only in before (breaking: removed; McpServerListItem, McpServerListItemEnvironment appeared in its place, likely a rename)
    - types resources::installations::CreateAccessGroupRequestBuilder — struct only in before (breaking: the new snapshot no longer has it)
    - types resources::installations::DeleteAccessGroupRequestBuilder — struct only in before (breaking: the new snapshot no longer has it)
    - types resources::installations::DeleteRequestBuilder — struct only in before (breaking: the new snapshot no longer has it)
    - types resources::installations::InstallationsResource — struct only in before (breaking: the new snapshot no longer has it)
    - types resources::installations::ListRequestBuilder — struct only in before (breaking: the new snapshot no longer has it)
    - types resources::installations::RetrieveRequestBuilder — struct only in before (breaking: the new snapshot no longer has it)
    - types resources::installations::UpdateRequestBuilder — struct only in before (breaking: the new snapshot no longer has it)
    - types resources::servers::DeleteRequestBuilder — struct only in before (breaking: the new snapshot no longer has it)
    - types resources::servers::RetrieveRequestBuilder — struct only in before (breaking: the new snapshot no longer has it)
    - types resources::servers::UpdateRequestBuilder — struct only in before (breaking: the new snapshot no longer has it)
    - fields models::McpServer.id — field only in before (breaking: removed; uid, domain, namespace appeared in its place, likely a rename)
    - fields models::McpServer.created_at — field retyped (breaking: changed in a way existing callers can observe)
    - fields models::McpServer.updated_at — field retyped (breaking: changed in a way existing callers can observe)
    - params models::McpServer.new/#3 — argument domain retyped (breaking: changed in a way existing callers can observe)
    - params models::McpServer.new/#4 — argument created_at retyped (breaking: changed in a way existing callers can observe)
    - params models::McpServer.new/#5 — new required argument updated_at in after; existing calls lack it (breaking: changed in a way existing callers can observe)
    - params models::McpServer.new/#6 — new required argument name in after; existing calls lack it (breaking: changed in a way existing callers can observe)
    - params models::McpServer.new — positional arguments moved (slug, created_at, updated_at, name); existing calls pass each value in another slot (breaking: changed in a way existing callers can observe)
    - fields models::ServersCreateResponse.installation — field only in before (breaking: the new snapshot no longer has it)
    - params models::ServersCreateResponse.new/#1 — argument installation only in before (breaking: the new snapshot no longer has it)
    - methods resources::servers::ListRequestBuilder.send — return type changed (breaking: changed in a way existing callers can observe)
    - methods resources::servers::ServersResource.delete — only in before (breaking: the new snapshot no longer has it)
    - methods resources::servers::ServersResource.installations — only in before (breaking: the new snapshot no longer has it)
    - methods resources::servers::ServersResource.retrieve — only in before (breaking: the new snapshot no longer has it)
    - methods resources::servers::ServersResource.update — only in before (breaking: the new snapshot no longer has it)
* **api:** 9 breaking changes to the SDK surface.
    - Added required property `sdk.current`.
    - Property `sdk.currentVersion` type changed from `version` to `string`.
    - Added required property `sdk.latestVersion`.
    - Removed optional property `sdk.apiVersion`.
    - Property `sdk_version.version` type changed from `version` to `string`.
    - Property `sdk_version.createdAt` is now required.
    - Removed required property `sdk_version.apiVersion`.
    - Removed required property `sdk_version.status`.
    - Removed optional property `sdk_version.publishedAt`.
* **api:** Added required property `github_project.chatInsightsEnabled`.
* **api:** 3 breaking changes to the SDK surface.
    - Property `api_document.tags` type changed from `string` to `unknown`.
    - Property `github_project.accessGroups` type changed from `string` to `unknown`.
    - Property `docs_project.accessGroups` type changed from `string` to `unknown`.
* **api:** 8 breaking changes to the SDK surface.
    - Removed body field `autoAddOperations` from `mcp.servers.update`.
    - Removed body field `isPrivate` from `mcp.servers.installations.update`.
    - Removed body field `loginPortalUid` from `mcp.servers.installations.update`.
    - Removed body field `documentAuth` from `mcp.servers.installations.update`.
    - Removed operation `mcp.servers.installations.create` (`POST /v1/mcp/servers/{id}/installations`).
    - Removed required property `mcp_server.autoAddOperations`.
    - Removed required property `mcp_installation.isPrivate`.
    - Removed required property `mcp_installation_list_item.isPrivate`.

### Features

* **api:** add property github_project.chatInsightsEnabled ([508357e](https://github.com/scalar/scalar-rs/commit/508357ea2f2441e6ff9f16a7ee6a7477abdd5b3b))
* **api:** add property sdk.current (+9 more changes) ([4022b30](https://github.com/scalar/scalar-rs/commit/4022b3002820eada65461cca14fa655b013996bb))
* **api:** update property api_document.tags (+3 more changes) ([b13635c](https://github.com/scalar/scalar-rs/commit/b13635c740fcc90a6b74601dd62d74ac4621f6e2))
* **api:** update SDK surface (14 changes) ([1df474b](https://github.com/scalar/scalar-rs/commit/1df474b3e059c2b97e247a1eb2fbd3d9f76f3a5a))
* **api:** update SDK surface (4 changes) ([64b74a6](https://github.com/scalar/scalar-rs/commit/64b74a6b1ff253ad0b0d49ea3e9f811525d3ebe5))
* **api:** update SDK surface (4 changes) ([1ec08c2](https://github.com/scalar/scalar-rs/commit/1ec08c2ddadb1805287e6280022d7d26c1fde3f5))
* **api:** update SDK surface (44 changes) ([2719c17](https://github.com/scalar/scalar-rs/commit/2719c17874f8a9ef5d8c85a015a879d4896c10e9))
* **api:** update SDK surface (7 changes) ([e83e8b9](https://github.com/scalar/scalar-rs/commit/e83e8b9f33037820be29c3916bf037dc4960b10a))


### Chores

* **api:** regenerate SDK ([d77e210](https://github.com/scalar/scalar-rs/commit/d77e21006f84ea17b61a5e8f57a865edfd83d080))
* **api:** regenerate SDK ([8abfdac](https://github.com/scalar/scalar-rs/commit/8abfdac7ef2b9a1be3f77787078d49991180b4c0))
* **api:** regenerate SDK ([d993dc4](https://github.com/scalar/scalar-rs/commit/d993dc4867a7f184b15d36946ecdb5458a21a820))
* **api:** regenerate SDK ([c419938](https://github.com/scalar/scalar-rs/commit/c4199383ff9f3183154f9357af36432d689dddcb))
* **api:** update generated SDK content ([fc874c1](https://github.com/scalar/scalar-rs/commit/fc874c16a73f8642bef7dde0c699a4862f547e8e))
* **api:** update generated SDK content ([612b335](https://github.com/scalar/scalar-rs/commit/612b335d511c4aaaacdba765b8a35b5c6850a35e))

## [0.4.0](https://github.com/scalar/scalar-rs/compare/v0.3.3...v0.4.0) (2026-10-09)


### ⚠ BREAKING CHANGES

* **api:** Schema `method` changed from `enum(delete | get | head | …)` to `string`.
* **api:** Configuration of `oauth2` auth scheme `OAuth2` changed.
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
* **api:** update auth scheme OAuth2 (+1 more change) ([ed639b9](https://github.com/scalar/scalar-rs/commit/ed639b9ec2da42e712f7466f896c27a903b6ad64))
* **api:** update property api_document.tags (+3 more changes) ([95d6e90](https://github.com/scalar/scalar-rs/commit/95d6e90e19d959d9968836b22efac74daaa3c835))
* **api:** update schema method ([1ec75c8](https://github.com/scalar/scalar-rs/commit/1ec75c8c3cc61afd8565462a23e8f755704c5129))
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
