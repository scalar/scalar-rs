# ScalarApi Rust API

## Types

- <code><a href="./reference.md">AccessGroup</a></code>
- <code><a href="./reference.md">ActiveDeployment</a></code>
- <code><a href="./reference.md">ApiDocument</a></code>
- <code><a href="./reference.md">BadRequestError</a></code>
- <code><a href="./reference.md">Email</a></code>
- <code><a href="./reference.md">ForbiddenError</a></code>
- <code><a href="./reference.md">GithubProject</a></code>
- <code><a href="./reference.md">GithubProjectRepository</a></code>
- <code><a href="./reference.md">InternalServerError</a></code>
- <code><a href="./reference.md">LoginPortal</a></code>
- <code><a href="./reference.md">LoginPortalEmail</a></code>
- <code><a href="./reference.md">LoginPortalPage</a></code>
- <code><a href="./reference.md">ManagedDocVersion</a></code>
- <code><a href="./reference.md">ManagedSchemaVersion</a></code>
- <code><a href="./reference.md">Method</a></code>
- <code><a href="./reference.md">Namespace</a></code>
- <code><a href="./reference.md">Nanoid</a></code>
- <code><a href="./reference.md">NotFoundError</a></code>
- <code><a href="./reference.md">Rule</a></code>
- <code><a href="./reference.md">Schema</a></code>
- <code><a href="./reference.md">Slug</a></code>
- <code><a href="./reference.md">Team</a></code>
- <code><a href="./reference.md">TeamImage</a></code>
- <code><a href="./reference.md">TeamName</a></code>
- <code><a href="./reference.md">TeamSummary</a></code>
- <code><a href="./reference.md">Theme</a></code>
- <code><a href="./reference.md">Timestamp</a></code>
- <code><a href="./reference.md">Uid</a></code>
- <code><a href="./reference.md">UnauthorizedError</a></code>
- <code><a href="./reference.md">UnprocessableEntityError</a></code>
- <code><a href="./reference.md">User</a></code>
- <code><a href="./reference.md">Version</a></code>

## Registry

Types:

- <code><a href="./reference.md">AccessGroup</a></code>
- <code><a href="./reference.md">ApiDocument</a></code>
- <code><a href="./reference.md">BadRequestError</a></code>
- <code><a href="./reference.md">ForbiddenError</a></code>
- <code><a href="./reference.md">InternalServerError</a></code>
- <code><a href="./reference.md">ManagedDocVersion</a></code>
- <code><a href="./reference.md">NotFoundError</a></code>
- <code><a href="./reference.md">UnauthorizedError</a></code>
- <code><a href="./reference.md">UnprocessableEntityError</a></code>
- <code><a href="./reference.md">Version</a></code>

Methods:

- <code title="GET /v1/apis">client.registry.<a href="./reference.md">listAllApiDocuments</a>(...)</code>
- <code title="GET /v1/apis/{namespace}">client.registry.<a href="./reference.md">listApiDocuments</a>(...)</code>
- <code title="POST /v1/apis/{namespace}">client.registry.<a href="./reference.md">createApiDocument</a>(...)</code>
- <code title="PATCH /v1/apis/{namespace}/{slug}">client.registry.<a href="./reference.md">updateApiDocument</a>(...)</code>
- <code title="DELETE /v1/apis/{namespace}/{slug}">client.registry.<a href="./reference.md">deleteApiDocument</a>(...)</code>
- <code title="GET /v1/apis/{namespace}/{slug}/version/{semver}">client.registry.<a href="./reference.md">retrieveApiDocumentVersion</a>(...)</code>
- <code title="PATCH /v1/apis/{namespace}/{slug}/version/{semver}">client.registry.<a href="./reference.md">updateApiDocumentVersion</a>(...)</code>
- <code title="DELETE /v1/apis/{namespace}/{slug}/version/{semver}">client.registry.<a href="./reference.md">deleteApiDocumentVersion</a>(...)</code>
- <code title="GET /v1/apis/{namespace}/{slug}/version/{semver}/metadata">client.registry.<a href="./reference.md">listApiDocumentVersionMetadata</a>(...) -&gt; managed_doc_version</code>
- <code title="POST /v1/apis/{namespace}/{slug}/version">client.registry.<a href="./reference.md">createApiDocumentVersion</a>(...) -&gt; managed_doc_version</code>
- <code title="POST /v1/apis/{namespace}/{slug}/access-group">client.registry.<a href="./reference.md">createApiDocumentAccessGroup</a>(...)</code>
- <code title="DELETE /v1/apis/{namespace}/{slug}/access-group">client.registry.<a href="./reference.md">deleteApiDocumentAccessGroup</a>(...)</code>

## Schemas

Types:

- <code><a href="./reference.md">BadRequestError</a></code>
- <code><a href="./reference.md">ForbiddenError</a></code>
- <code><a href="./reference.md">InternalServerError</a></code>
- <code><a href="./reference.md">NotFoundError</a></code>
- <code><a href="./reference.md">Schema</a></code>
- <code><a href="./reference.md">Uid</a></code>
- <code><a href="./reference.md">UnauthorizedError</a></code>
- <code><a href="./reference.md">UnprocessableEntityError</a></code>
- <code><a href="./reference.md">Version</a></code>

Methods:

- <code title="GET /v1/schemas/{namespace}">client.schemas.<a href="./reference.md">list</a>(...)</code>
- <code title="POST /v1/schemas/{namespace}">client.schemas.<a href="./reference.md">create</a>(...) -&gt; uid</code>
- <code title="PATCH /v1/schemas/{namespace}/{slug}">client.schemas.<a href="./reference.md">update</a>(...)</code>
- <code title="DELETE /v1/schemas/{namespace}/{slug}">client.schemas.<a href="./reference.md">delete</a>(...)</code>

### Version

Types:

- <code><a href="./reference.md">BadRequestError</a></code>
- <code><a href="./reference.md">ForbiddenError</a></code>
- <code><a href="./reference.md">InternalServerError</a></code>
- <code><a href="./reference.md">NotFoundError</a></code>
- <code><a href="./reference.md">Uid</a></code>
- <code><a href="./reference.md">UnauthorizedError</a></code>
- <code><a href="./reference.md">UnprocessableEntityError</a></code>
- <code><a href="./reference.md">Version</a></code>

Methods:

- <code title="GET /v1/schemas/{namespace}/{slug}/version/{semver}">client.schemas.version.<a href="./reference.md">retrieveSchema</a>(...)</code>
- <code title="DELETE /v1/schemas/{namespace}/{slug}/version/{semver}">client.schemas.version.<a href="./reference.md">deleteSchema</a>(...)</code>
- <code title="POST /v1/schemas/{namespace}/{slug}/version">client.schemas.version.<a href="./reference.md">createSchema</a>(...) -&gt; uid</code>

### AccessGroup

Types:

- <code><a href="./reference.md">AccessGroup</a></code>
- <code><a href="./reference.md">BadRequestError</a></code>
- <code><a href="./reference.md">ForbiddenError</a></code>
- <code><a href="./reference.md">InternalServerError</a></code>
- <code><a href="./reference.md">NotFoundError</a></code>
- <code><a href="./reference.md">UnauthorizedError</a></code>
- <code><a href="./reference.md">UnprocessableEntityError</a></code>

Methods:

- <code title="POST /v1/schemas/{namespace}/{slug}/access-group">client.schemas.accessGroup.<a href="./reference.md">createSchema</a>(...)</code>
- <code title="DELETE /v1/schemas/{namespace}/{slug}/access-group">client.schemas.accessGroup.<a href="./reference.md">deleteSchema</a>(...)</code>

## LoginPortals

Types:

- <code><a href="./reference.md">BadRequestError</a></code>
- <code><a href="./reference.md">ForbiddenError</a></code>
- <code><a href="./reference.md">InternalServerError</a></code>
- <code><a href="./reference.md">LoginPortal</a></code>
- <code><a href="./reference.md">LoginPortalEmail</a></code>
- <code><a href="./reference.md">LoginPortalPage</a></code>
- <code><a href="./reference.md">NotFoundError</a></code>
- <code><a href="./reference.md">Uid</a></code>
- <code><a href="./reference.md">UnauthorizedError</a></code>
- <code><a href="./reference.md">UnprocessableEntityError</a></code>

Methods:

- <code title="GET /v1/login-portals/{slug}">client.loginPortals.<a href="./reference.md">retrieve</a>(...)</code>
- <code title="PATCH /v1/login-portals/{slug}">client.loginPortals.<a href="./reference.md">update</a>(...)</code>
- <code title="DELETE /v1/login-portals/{slug}">client.loginPortals.<a href="./reference.md">delete</a>(...)</code>
- <code title="POST /v1/login-portals">client.loginPortals.<a href="./reference.md">create</a>(...) -&gt; uid</code>
- <code title="GET /v1/login-portals">client.loginPortals.<a href="./reference.md">list</a>(...)</code>

## Rules

Types:

- <code><a href="./reference.md">AccessGroup</a></code>
- <code><a href="./reference.md">BadRequestError</a></code>
- <code><a href="./reference.md">ForbiddenError</a></code>
- <code><a href="./reference.md">InternalServerError</a></code>
- <code><a href="./reference.md">NotFoundError</a></code>
- <code><a href="./reference.md">Rule</a></code>
- <code><a href="./reference.md">Uid</a></code>
- <code><a href="./reference.md">UnauthorizedError</a></code>
- <code><a href="./reference.md">UnprocessableEntityError</a></code>

Methods:

- <code title="GET /v1/rulesets/{namespace}">client.rules.<a href="./reference.md">listRulesets</a>(...)</code>
- <code title="POST /v1/rulesets/{namespace}">client.rules.<a href="./reference.md">createRuleset</a>(...) -&gt; uid</code>
- <code title="PATCH /v1/rulesets/{namespace}/{slug}">client.rules.<a href="./reference.md">updateRuleset</a>(...)</code>
- <code title="DELETE /v1/rulesets/{namespace}/{slug}">client.rules.<a href="./reference.md">deleteRuleset</a>(...)</code>
- <code title="GET /v1/rulesets/{namespace}/{slug}">client.rules.<a href="./reference.md">retrieveRulesetDocument</a>(...)</code>
- <code title="POST /v1/rulesets/{namespace}/{slug}/access-group">client.rules.<a href="./reference.md">createRulesetAccessGroup</a>(...)</code>
- <code title="DELETE /v1/rulesets/{namespace}/{slug}/access-group">client.rules.<a href="./reference.md">deleteRulesetAccessGroup</a>(...)</code>

## Themes

Types:

- <code><a href="./reference.md">BadRequestError</a></code>
- <code><a href="./reference.md">ForbiddenError</a></code>
- <code><a href="./reference.md">InternalServerError</a></code>
- <code><a href="./reference.md">NotFoundError</a></code>
- <code><a href="./reference.md">Theme</a></code>
- <code><a href="./reference.md">Uid</a></code>
- <code><a href="./reference.md">UnauthorizedError</a></code>
- <code><a href="./reference.md">UnprocessableEntityError</a></code>

Methods:

- <code title="GET /v1/themes">client.themes.<a href="./reference.md">list</a>(...)</code>
- <code title="POST /v1/themes">client.themes.<a href="./reference.md">create</a>(...) -&gt; uid</code>
- <code title="PATCH /v1/themes/{slug}">client.themes.<a href="./reference.md">update</a>(...)</code>
- <code title="PUT /v1/themes/{slug}">client.themes.<a href="./reference.md">replaceDocument</a>(...)</code>
- <code title="DELETE /v1/themes/{slug}">client.themes.<a href="./reference.md">delete</a>(...)</code>
- <code title="GET /v1/themes/{slug}">client.themes.<a href="./reference.md">retrieve</a>(...)</code>

## Teams

Types:

- <code><a href="./reference.md">BadRequestError</a></code>
- <code><a href="./reference.md">ForbiddenError</a></code>
- <code><a href="./reference.md">InternalServerError</a></code>
- <code><a href="./reference.md">NotFoundError</a></code>
- <code><a href="./reference.md">Team</a></code>
- <code><a href="./reference.md">UnauthorizedError</a></code>
- <code><a href="./reference.md">UnprocessableEntityError</a></code>

Methods:

- <code title="GET /v1/teams">client.teams.<a href="./reference.md">list</a>(...)</code>

## ScalarDocs

Types:

- <code><a href="./reference.md">BadRequestError</a></code>
- <code><a href="./reference.md">ForbiddenError</a></code>
- <code><a href="./reference.md">GithubProject</a></code>
- <code><a href="./reference.md">InternalServerError</a></code>
- <code><a href="./reference.md">NotFoundError</a></code>
- <code><a href="./reference.md">Slug</a></code>
- <code><a href="./reference.md">UnauthorizedError</a></code>
- <code><a href="./reference.md">UnprocessableEntityError</a></code>

Methods:

- <code title="GET /v1/guides">client.scalarDocs.<a href="./reference.md">listGuides</a>(...)</code>
- <code title="POST /v1/guides">client.scalarDocs.<a href="./reference.md">createGuide</a>(...)</code>
- <code title="POST /v1/guides/{slug}/publish">client.scalarDocs.<a href="./reference.md">publishGuide</a>(...)</code>

## Namespaces

Types:

- <code><a href="./reference.md">BadRequestError</a></code>
- <code><a href="./reference.md">ForbiddenError</a></code>
- <code><a href="./reference.md">InternalServerError</a></code>
- <code><a href="./reference.md">NotFoundError</a></code>
- <code><a href="./reference.md">UnauthorizedError</a></code>
- <code><a href="./reference.md">UnprocessableEntityError</a></code>

Methods:

- <code title="GET /v1/namespaces">client.namespaces.<a href="./reference.md">list</a>(...)</code>

## Authentication

Types:

- <code><a href="./reference.md">BadRequestError</a></code>
- <code><a href="./reference.md">ForbiddenError</a></code>
- <code><a href="./reference.md">InternalServerError</a></code>
- <code><a href="./reference.md">NotFoundError</a></code>
- <code><a href="./reference.md">UnauthorizedError</a></code>
- <code><a href="./reference.md">UnprocessableEntityError</a></code>
- <code><a href="./reference.md">User</a></code>

Methods:

- <code title="POST /v1/auth/exchange">client.authentication.<a href="./reference.md">exchangePersonalToken</a>(...)</code>
- <code title="GET /v1/auth/me">client.authentication.<a href="./reference.md">listCurrentUser</a>(...) -&gt; user</code>
