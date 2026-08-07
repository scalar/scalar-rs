# ScalarApi Rust SDK Reference

## Operations

### registry.listAllApiDocuments

List all API Documents

- HTTP: `GET /v1/apis`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### registry.listApiDocuments

List API Documents in a namespace

- HTTP: `GET /v1/apis/{namespace}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### registry.createApiDocument

Create API Document

- HTTP: `POST /v1/apis/{namespace}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### registry.updateApiDocument

Update API Document metadata

- HTTP: `PATCH /v1/apis/{namespace}/{slug}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### registry.deleteApiDocument

Delete API Document

- HTTP: `DELETE /v1/apis/{namespace}/{slug}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### registry.retrieveApiDocumentVersion

Get API Document

- HTTP: `GET /v1/apis/{namespace}/{slug}/version/{semver}`
- Response body: `text/plain`
- Errors: `400, 401, 403, 404, 422, 500`

### registry.updateApiDocumentVersion

Update API Document version

- HTTP: `PATCH /v1/apis/{namespace}/{slug}/version/{semver}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### registry.deleteApiDocumentVersion

Delete API Document version

- HTTP: `DELETE /v1/apis/{namespace}/{slug}/version/{semver}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### registry.listApiDocumentVersionMetadata

Get API Document version metadata

- HTTP: `GET /v1/apis/{namespace}/{slug}/version/{semver}/metadata`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### registry.createApiDocumentVersion

Create API Document version

- HTTP: `POST /v1/apis/{namespace}/{slug}/version`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### registry.createApiDocumentAccessGroup

Add access group

- HTTP: `POST /v1/apis/{namespace}/{slug}/access-group`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### registry.deleteApiDocumentAccessGroup

Remove access group

- HTTP: `DELETE /v1/apis/{namespace}/{slug}/access-group`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### schemas.list

List all shared components

- HTTP: `GET /v1/schemas/{namespace}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### schemas.create

Create a shared component

- HTTP: `POST /v1/schemas/{namespace}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### schemas.update

Update shared component metadata

- HTTP: `PATCH /v1/schemas/{namespace}/{slug}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### schemas.delete

Delete a shared component

- HTTP: `DELETE /v1/schemas/{namespace}/{slug}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### schemas.version.retrieveSchema

Get a shared component document

- HTTP: `GET /v1/schemas/{namespace}/{slug}/version/{semver}`
- Response body: `text/plain`
- Errors: `400, 401, 403, 404, 422, 500`

### schemas.version.deleteSchema

Delete a shared component version

- HTTP: `DELETE /v1/schemas/{namespace}/{slug}/version/{semver}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### schemas.version.createSchema

Create a shared component version

- HTTP: `POST /v1/schemas/{namespace}/{slug}/version`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### schemas.accessGroup.createSchema

Add shared component access group

- HTTP: `POST /v1/schemas/{namespace}/{slug}/access-group`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### schemas.accessGroup.deleteSchema

Remove shared component access group

- HTTP: `DELETE /v1/schemas/{namespace}/{slug}/access-group`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### loginPortals.retrieve

Get a login portal

- HTTP: `GET /v1/login-portals/{slug}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### loginPortals.update

Update portal metadata

- HTTP: `PATCH /v1/login-portals/{slug}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### loginPortals.delete

Delete a login portal

- HTTP: `DELETE /v1/login-portals/{slug}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### loginPortals.create

Create a portal

- HTTP: `POST /v1/login-portals`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### loginPortals.list

List all portals

- HTTP: `GET /v1/login-portals`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### rules.listRulesets

List all rules

- HTTP: `GET /v1/rulesets/{namespace}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### rules.createRuleset

Create a rule

- HTTP: `POST /v1/rulesets/{namespace}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### rules.updateRuleset

Update rule metadata

- HTTP: `PATCH /v1/rulesets/{namespace}/{slug}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### rules.deleteRuleset

Delete a rule

- HTTP: `DELETE /v1/rulesets/{namespace}/{slug}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### rules.retrieveRulesetDocument

Get a rule

- HTTP: `GET /v1/rulesets/{namespace}/{slug}`
- Response body: `text/plain`
- Errors: `400, 401, 403, 404, 422, 500`

### rules.createRulesetAccessGroup

Add rule access group

- HTTP: `POST /v1/rulesets/{namespace}/{slug}/access-group`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### rules.deleteRulesetAccessGroup

Remove rule access group

- HTTP: `DELETE /v1/rulesets/{namespace}/{slug}/access-group`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### themes.list

List all themes

- HTTP: `GET /v1/themes`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### themes.create

Create a theme

- HTTP: `POST /v1/themes`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### themes.update

Update theme metadata

- HTTP: `PATCH /v1/themes/{slug}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### themes.replaceDocument

Update theme document

- HTTP: `PUT /v1/themes/{slug}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### themes.delete

Delete a theme

- HTTP: `DELETE /v1/themes/{slug}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### themes.retrieve

Get a theme

- HTTP: `GET /v1/themes/{slug}`
- Response body: `text/plain`
- Errors: `400, 401, 403, 404, 422, 500`

### teams.list

List teams

- HTTP: `GET /v1/teams`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### scalarDocs.listGuides

List all projects

- HTTP: `GET /v1/guides`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### scalarDocs.createGuide

Create a project

- HTTP: `POST /v1/guides`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### scalarDocs.publishGuide

Publish a project

- HTTP: `POST /v1/guides/{slug}/publish`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### namespaces.list

List namespaces

- HTTP: `GET /v1/namespaces`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### authentication.exchangePersonalToken

Exchange token

- HTTP: `POST /v1/auth/exchange`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### authentication.listCurrentUser

Get current user

- HTTP: `GET /v1/auth/me`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

## Models

- `BadRequestError`
- `UnauthorizedError`
- `ForbiddenError`
- `NotFoundError`
- `UnprocessableEntityError`
- `InternalServerError`
- `ApiDocument`
- `Nanoid`
- `Version`
- `Slug`
- `Namespace`
- `ManagedDocVersion`
- `Method`
- `AccessGroup`
- `Schema`
- `ManagedSchemaVersion`
- `Timestamp`
- `Uid`
- `LoginPortalEmail`
- `LoginPortalPage`
- `LoginPortal`
- `Rule`
- `Theme`
- `Team`
- `TeamName`
- `TeamImage`
- `GithubProject`
- `ActiveDeployment`
- `GithubProjectRepository`
- `Email`
- `TeamSummary`
- `User`
