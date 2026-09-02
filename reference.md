# Scalar Rust SDK Reference

## Operations

### client.registry().list_all_api_documents()

List all API Documents

- HTTP: `GET /v1/apis`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.registry().list_api_documents(…)

List API Documents in a namespace

- HTTP: `GET /v1/apis/{namespace}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.registry().create_api_document(…)

Create API Document

- HTTP: `POST /v1/apis/{namespace}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.registry().update_api_document(…)

Update API Document metadata

- HTTP: `PATCH /v1/apis/{namespace}/{slug}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.registry().delete_api_document(…)

Delete API Document

- HTTP: `DELETE /v1/apis/{namespace}/{slug}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.registry().retrieve_api_document_version(…)

Get API Document

- HTTP: `GET /v1/apis/{namespace}/{slug}/version/{semver}`
- Response body: `text/plain`
- Errors: `400, 401, 403, 404, 422, 500`

### client.registry().update_api_document_version(…)

Update API Document version

- HTTP: `PATCH /v1/apis/{namespace}/{slug}/version/{semver}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.registry().delete_api_document_version(…)

Delete API Document version

- HTTP: `DELETE /v1/apis/{namespace}/{slug}/version/{semver}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.registry().list_api_document_version_metadata(…)

Get API Document version metadata

- HTTP: `GET /v1/apis/{namespace}/{slug}/version/{semver}/metadata`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.registry().create_api_document_version(…)

Create API Document version

- HTTP: `POST /v1/apis/{namespace}/{slug}/version`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.registry().create_api_document_access_group(…)

Add access group

- HTTP: `POST /v1/apis/{namespace}/{slug}/access-group`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.registry().delete_api_document_access_group(…)

Remove access group

- HTTP: `DELETE /v1/apis/{namespace}/{slug}/access-group`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.schemas().list(…)

List all shared components

- HTTP: `GET /v1/schemas/{namespace}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.schemas().create(…)

Create a shared component

- HTTP: `POST /v1/schemas/{namespace}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.schemas().update(…)

Update shared component metadata

- HTTP: `PATCH /v1/schemas/{namespace}/{slug}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.schemas().delete(…)

Delete a shared component

- HTTP: `DELETE /v1/schemas/{namespace}/{slug}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.schemas().version().retrieve(…)

Get a shared component document

- HTTP: `GET /v1/schemas/{namespace}/{slug}/version/{semver}`
- Response body: `text/plain`
- Errors: `400, 401, 403, 404, 422, 500`

### client.schemas().version().delete(…)

Delete a shared component version

- HTTP: `DELETE /v1/schemas/{namespace}/{slug}/version/{semver}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.schemas().version().create(…)

Create a shared component version

- HTTP: `POST /v1/schemas/{namespace}/{slug}/version`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.schemas().access_group().create(…)

Add shared component access group

- HTTP: `POST /v1/schemas/{namespace}/{slug}/access-group`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.schemas().access_group().delete(…)

Remove shared component access group

- HTTP: `DELETE /v1/schemas/{namespace}/{slug}/access-group`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.login_portals().retrieve(…)

Get a login portal

- HTTP: `GET /v1/login-portals/{slug}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.login_portals().update(…)

Update portal metadata

- HTTP: `PATCH /v1/login-portals/{slug}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.login_portals().delete(…)

Delete a login portal

- HTTP: `DELETE /v1/login-portals/{slug}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.login_portals().create(…)

Create a portal

- HTTP: `POST /v1/login-portals`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.login_portals().list()

List all portals

- HTTP: `GET /v1/login-portals`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.rules().list_rulesets(…)

List all rules

- HTTP: `GET /v1/rulesets/{namespace}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.rules().create_ruleset(…)

Create a rule

- HTTP: `POST /v1/rulesets/{namespace}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.rules().update_ruleset(…)

Update rule metadata

- HTTP: `PATCH /v1/rulesets/{namespace}/{slug}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.rules().delete_ruleset(…)

Delete a rule

- HTTP: `DELETE /v1/rulesets/{namespace}/{slug}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.rules().retrieve_ruleset_document(…)

Get a rule

- HTTP: `GET /v1/rulesets/{namespace}/{slug}`
- Response body: `text/plain`
- Errors: `400, 401, 403, 404, 422, 500`

### client.rules().create_ruleset_access_group(…)

Add rule access group

- HTTP: `POST /v1/rulesets/{namespace}/{slug}/access-group`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.rules().delete_ruleset_access_group(…)

Remove rule access group

- HTTP: `DELETE /v1/rulesets/{namespace}/{slug}/access-group`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.themes().list()

List all themes

- HTTP: `GET /v1/themes`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.themes().create(…)

Create a theme

- HTTP: `POST /v1/themes`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.themes().update(…)

Update theme metadata

- HTTP: `PATCH /v1/themes/{slug}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.themes().replace_document(…)

Update theme document

- HTTP: `PUT /v1/themes/{slug}`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.themes().delete(…)

Delete a theme

- HTTP: `DELETE /v1/themes/{slug}`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.themes().retrieve(…)

Get a theme

- HTTP: `GET /v1/themes/{slug}`
- Response body: `text/plain`
- Errors: `400, 401, 403, 404, 422, 500`

### client.teams().list()

List teams

- HTTP: `GET /v1/teams`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.scalar_docs().list_guides()

List all projects

- HTTP: `GET /v1/guides`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.scalar_docs().create_guide(…)

Create a project

- HTTP: `POST /v1/guides`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.scalar_docs().publish_guide(…)

Publish a project

- HTTP: `POST /v1/guides/{slug}/publish`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.namespaces().list()

List namespaces

- HTTP: `GET /v1/namespaces`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.authentication().exchange_personal_token(…)

Exchange token

- HTTP: `POST /v1/auth/exchange`
- Request body: `application/json`
- Response body: `application/json`
- Errors: `400, 401, 403, 404, 422, 500`

### client.authentication().list_current_user()

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
