# Scalar Rust API

Complete reference of every operation, grouped by resource. See [the README](./README.md) for usage and configuration.

## Contents

- [`Registry`](#registry)
  - [List all API Documents](#list-all-api-documents)
  - [List API Documents in a namespace](#list-api-documents-in-a-namespace)
  - [Create API Document](#create-api-document)
  - [Update API Document metadata](#update-api-document-metadata)
  - [Delete API Document](#delete-api-document)
  - [Get API Document](#get-api-document)
  - [Update API Document version](#update-api-document-version)
  - [Delete API Document version](#delete-api-document-version)
  - [Get API Document version metadata](#get-api-document-version-metadata)
  - [Create API Document version](#create-api-document-version)
  - [Add access group](#add-access-group)
  - [Remove access group](#remove-access-group)
- [`Schemas`](#schemas)
  - [List all shared components](#list-all-shared-components)
  - [Create a shared component](#create-a-shared-component)
  - [Update shared component metadata](#update-shared-component-metadata)
  - [Delete a shared component](#delete-a-shared-component)
  - [`Schemas Version`](#schemas-version)
    - [Get a shared component document](#get-a-shared-component-document)
    - [Delete a shared component version](#delete-a-shared-component-version)
    - [Create a shared component version](#create-a-shared-component-version)
  - [`Schemas AccessGroup`](#schemas-accessgroup)
    - [Add shared component access group](#add-shared-component-access-group)
    - [Remove shared component access group](#remove-shared-component-access-group)
- [`LoginPortals`](#loginportals)
  - [Get a login portal](#get-a-login-portal)
  - [Update portal metadata](#update-portal-metadata)
  - [Delete a login portal](#delete-a-login-portal)
  - [Create a portal](#create-a-portal)
  - [List all portals](#list-all-portals)
- [`AccessGroups`](#accessgroups)
  - [Create an access group](#create-an-access-group)
  - [Get an access group](#get-an-access-group)
  - [Update an access group](#update-an-access-group)
  - [Delete an access group](#delete-an-access-group)
  - [`AccessGroups Domains`](#accessgroups-domains)
    - [Add an allowed email domain](#add-an-allowed-email-domain)
    - [Remove an allowed email domain](#remove-an-allowed-email-domain)
- [`Rules`](#rules)
  - [List all rules](#list-all-rules)
  - [Create a rule](#create-a-rule)
  - [Update rule metadata](#update-rule-metadata)
  - [Delete a rule](#delete-a-rule)
  - [Get a rule](#get-a-rule)
  - [Add rule access group](#add-rule-access-group)
  - [Remove rule access group](#remove-rule-access-group)
- [`Themes`](#themes)
  - [List all themes](#list-all-themes)
  - [Create a theme](#create-a-theme)
  - [Update theme metadata](#update-theme-metadata)
  - [Update theme document](#update-theme-document)
  - [Delete a theme](#delete-a-theme)
  - [Get a theme](#get-a-theme)
- [`Teams`](#teams)
  - [List teams](#list-teams)
  - [`Teams Members`](#teams-members)
    - [List team members](#list-team-members)
    - [Change a member role](#change-a-member-role)
    - [Remove a member](#remove-a-member)
  - [`Teams Invites`](#teams-invites)
    - [Invite a member](#invite-a-member)
    - [Resend an invite](#resend-an-invite)
    - [Cancel an invite](#cancel-an-invite)
- [`ScalarDocs`](#scalardocs)
  - [List all projects](#list-all-projects)
  - [Create a project](#create-a-project)
  - [Publish a project](#publish-a-project)
  - [List all docs projects](#list-all-docs-projects)
  - [Create a docs project](#create-a-docs-project)
  - [Get a docs project](#get-a-docs-project)
  - [Update a docs project](#update-a-docs-project)
  - [Delete a docs project](#delete-a-docs-project)
  - [Publish a docs project](#publish-a-docs-project)
  - [Read the site config](#read-the-site-config)
  - [Write the site config](#write-the-site-config)
  - [Get the site domains](#get-the-site-domains)
  - [Check domain DNS](#check-domain-dns)
- [`Namespaces`](#namespaces)
  - [List namespaces](#list-namespaces)
- [`Authentication`](#authentication)
  - [Exchange token](#exchange-token)
  - [Get current user](#get-current-user)
- [`Sdks`](#sdks)
  - [List all SDKs](#list-all-sdks)
  - [Create an SDK](#create-an-sdk)
  - [Get an SDK](#get-an-sdk)
  - [Update an SDK](#update-an-sdk)
  - [Delete an SDK](#delete-an-sdk)
  - [Build an SDK](#build-an-sdk)
  - [`Sdks Versions`](#sdks-versions)
    - [Create an SDK version](#create-an-sdk-version)
    - [Delete an SDK version](#delete-an-sdk-version)
  - [`Sdks Repositories`](#sdks-repositories)
    - [Link a repository](#link-a-repository)
    - [Unlink a repository](#unlink-a-repository)
    - [Update publishing settings](#update-publishing-settings)
- [`Mcp`](#mcp)
  - [`Mcp Servers`](#mcp-servers)
    - [List all MCP servers](#list-all-mcp-servers)
    - [Create an MCP server](#create-an-mcp-server)
    - [Get an MCP server](#get-an-mcp-server)
    - [Update an MCP server](#update-an-mcp-server)
    - [Delete an MCP server](#delete-an-mcp-server)
    - [`Mcp Servers Installations`](#mcp-servers-installations)
      - [List installations](#list-installations)
      - [Create an installation](#create-an-installation)
      - [Get an installation](#get-an-installation)
      - [Update an installation](#update-an-installation)
      - [Delete an installation](#delete-an-installation)
      - [Add an access group](#add-an-access-group)
      - [Remove an access group](#remove-an-access-group)
- [`OAuth`](#oauth)
  - [Start an OAuth authorization](#start-an-oauth-authorization)
  - [Exchange a code or refresh token](#exchange-a-code-or-refresh-token)
  - [Revoke a refresh token](#revoke-a-refresh-token)
  - [Authorization server metadata](#authorization-server-metadata)

## Setup

```rust
use scalar_rs::*;

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    let client = Scalar::from_env()?;

    // ... the samples below go here

    Ok(())
}
```

## `Registry`

Registry

### List all API Documents

List all API documents across every namespace the caller can access.

| Direction | Type |
| --- | --- |
| Response | [`Vec<ApiDocument>`](./src/models/registry.rs) |

```rust
let response = client.registry().list_all_api_documents().send().await?;
```

### List API Documents in a namespace

List API documents in a namespace.

| Direction | Type |
| --- | --- |
| Response | [`Vec<ApiDocument>`](./src/models/registry.rs) |

```rust
let response = client.registry().list_api_documents("acme").send().await?;
```

### Create API Document

Create an API document.

| Direction | Type |
| --- | --- |
| Request | [`RegistryCreateApiDocumentBody`](./src/models/registry.rs) |
| Response | [`RegistryCreateApiDocumentResponse`](./src/models/registry.rs) |

```rust
let response = client
    .registry()
    .create_api_document(
        "acme",
        RegistryCreateApiDocumentBody {
            title: "Acme API".to_string(),
            description: None,
            version: "1.2.0".to_string(),
            slug: "acme-api".to_string(),
            ruleset: None,
            is_private: None,
            document:
                "{\"openapi\":\"3.1.0\",\"info\":{\"title\":\"Acme API\",\"version\":\"1.2.0\"},\"paths\":{}}"
                    .to_string(),
        },
    )
    .send()
    .await?;
```

### Update API Document metadata

Update metadata for an API document.

| Direction | Type |
| --- | --- |
| Request | [`RegistryUpdateApiDocumentBody`](./src/models/registry.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .registry()
    .update_api_document(
        "acme",
        "acme-api",
        RegistryUpdateApiDocumentBody {
            title: None,
            description: None,
            is_private: None,
            ruleset: None,
        },
    )
    .send()
    .await?;
```

### Delete API Document

Delete an API document and all versions.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.registry().delete_api_document("acme", "acme-api").send().await?;
```

### Get API Document

Get a specific API document version.

| Direction | Type |
| --- | --- |
| Response | `bytes::Bytes` |

```rust
let response = client
    .registry()
    .retrieve_api_document_version("acme", "acme-api", "1.2.0")
    .send()
    .await?;
```

### Update API Document version

Update the registry file content for an API document version.

| Direction | Type |
| --- | --- |
| Request | [`RegistryUpdateApiDocumentVersionBody`](./src/models/registry.rs) |
| Response | [`RegistryUpdateApiDocumentVersionResponse`](./src/models/registry.rs) |

```rust
let response = client
    .registry()
    .update_api_document_version(
        "acme",
        "acme-api",
        "1.2.0",
        RegistryUpdateApiDocumentVersionBody {
            document:
                "{\"openapi\":\"3.1.0\",\"info\":{\"title\":\"Acme API\",\"version\":\"1.2.0\"},\"paths\":{}}"
                    .to_string(),
        },
    )
    .send()
    .await?;
```

### Delete API Document version

Delete a specific API document version.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client
    .registry()
    .delete_api_document_version("acme", "acme-api", "1.2.0")
    .send()
    .await?;
```

### Get API Document version metadata

Get metadata (uid, content shas, version sha, tags) for a specific API document version.

| Direction | Type |
| --- | --- |
| Response | [`ManagedDocVersion`](./src/models/shared.rs) |

```rust
let response = client
    .registry()
    .list_api_document_version_metadata("acme", "acme-api", "1.2.0")
    .send()
    .await?;
```

### Create API Document version

Create a new API document version.

| Direction | Type |
| --- | --- |
| Request | [`RegistryCreateApiDocumentVersionBody`](./src/models/registry.rs) |
| Response | [`ManagedDocVersion`](./src/models/shared.rs) |

```rust
let response = client
    .registry()
    .create_api_document_version(
        "acme",
        "acme-api",
        RegistryCreateApiDocumentVersionBody {
            version: "1.2.0".to_string(),
            document:
                "{\"openapi\":\"3.1.0\",\"info\":{\"title\":\"Acme API\",\"version\":\"1.2.0\"},\"paths\":{}}"
                    .to_string(),
            force: None,
        },
    )
    .send()
    .await?;
```

### Add access group

Add an access group to an API document.

| Direction | Type |
| --- | --- |
| Request | [`AccessGroup`](./src/models/registry.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .registry()
    .create_api_document_access_group(
        "acme",
        "acme-api",
        AccessGroup {
            access_group_slug: "acme-api".to_string(),
        },
    )
    .send()
    .await?;
```

### Remove access group

Remove an access group from an API document.

| Direction | Type |
| --- | --- |
| Request | [`AccessGroup`](./src/models/registry.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .registry()
    .delete_api_document_access_group(
        "acme",
        "acme-api",
        AccessGroup {
            access_group_slug: "acme-api".to_string(),
        },
    )
    .send()
    .await?;
```

## `Schemas`

Schemas

### List all shared components

List schemas in a namespace.

| Direction | Type |
| --- | --- |
| Response | [`Vec<Schema>`](./src/models/schemas.rs) |

```rust
let response = client.schemas().list("acme").send().await?;
```

### Create a shared component

Create a schema in a namespace.

| Direction | Type |
| --- | --- |
| Request | [`SchemasCreateBody`](./src/models/schemas.rs) |
| Response | [`Uid`](./src/models/shared.rs) |

```rust
let response = client
    .schemas()
    .create(
        "acme",
        SchemasCreateBody {
            title: "Customer".to_string(),
            description: None,
            version: "1.2.0".to_string(),
            slug: "customer".to_string(),
            is_private: None,
            document:
                "{\"type\":\"object\",\"properties\":{\"name\":{\"type\":\"string\",\"examples\":[\"Acme\"]}}}"
                    .to_string(),
        },
    )
    .send()
    .await?;
```

### Update shared component metadata

Update schema metadata.

| Direction | Type |
| --- | --- |
| Request | [`SchemasUpdateBody`](./src/models/schemas.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .schemas()
    .update(
        "acme",
        "customer",
        SchemasUpdateBody {
            title: None,
            description: None,
            is_private: None,
        },
    )
    .send()
    .await?;
```

### Delete a shared component

Delete a schema and all related versions.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.schemas().delete("acme", "customer").send().await?;
```

### `Schemas Version`

Schemas

#### Get a shared component document

Get a specific schema version document.

| Direction | Type |
| --- | --- |
| Response | `bytes::Bytes` |

```rust
let response = client
    .schemas()
    .version()
    .retrieve("acme", "customer", "1.2.0")
    .send()
    .await?;
```

#### Delete a shared component version

Delete a schema version.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client
    .schemas()
    .version()
    .delete("acme", "customer", "1.2.0")
    .send()
    .await?;
```

#### Create a shared component version

Create a schema version.

| Direction | Type |
| --- | --- |
| Request | [`VersionCreateBody`](./src/models/version.rs) |
| Response | [`VersionCreateResponse`](./src/models/version.rs) |

```rust
let response = client
    .schemas()
    .version()
    .create(
        "acme",
        "customer",
        VersionCreateBody {
            version: "1.2.0".to_string(),
            document:
                "{\"type\":\"object\",\"properties\":{\"name\":{\"type\":\"string\",\"examples\":[\"Acme\"]}}}"
                    .to_string(),
            force: None,
        },
    )
    .send()
    .await?;
```

### `Schemas AccessGroup`

Schemas

#### Add shared component access group

Add an access group to a schema.

| Direction | Type |
| --- | --- |
| Request | [`AccessGroup`](./src/models/registry.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .schemas()
    .access_group()
    .create(
        "acme",
        "customer",
        AccessGroup {
            access_group_slug: "acme-api".to_string(),
        },
    )
    .send()
    .await?;
```

#### Remove shared component access group

Remove an access group from a schema.

| Direction | Type |
| --- | --- |
| Request | [`AccessGroup`](./src/models/registry.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .schemas()
    .access_group()
    .delete(
        "acme",
        "customer",
        AccessGroup {
            access_group_slug: "acme-api".to_string(),
        },
    )
    .send()
    .await?;
```

## `LoginPortals`

Login Portals

### Get a login portal

Get a login portal by slug.

| Direction | Type |
| --- | --- |
| Response | [`LoginPortalsRetrieveResponse`](./src/models/login_portals.rs) |

```rust
let response = client.login_portals().retrieve("acme-login").send().await?;
```

### Update portal metadata

Update metadata for a login portal.

| Direction | Type |
| --- | --- |
| Request | [`LoginPortalsUpdateBody`](./src/models/login_portals.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .login_portals()
    .update("acme-login", LoginPortalsUpdateBody { title: None })
    .send()
    .await?;
```

### Delete a login portal

Delete a login portal.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.login_portals().delete("acme-login").send().await?;
```

### Create a portal

Create a login portal for the current team.

| Direction | Type |
| --- | --- |
| Request | [`LoginPortalsCreateBody`](./src/models/login_portals.rs) |
| Response | [`Uid`](./src/models/shared.rs) |

```rust
let response = client
    .login_portals()
    .create(LoginPortalsCreateBody {
        title: "Acme Private Documentation".to_string(),
        slug: "acme-login".to_string(),
        email: LoginPortalEmail {
            logo: "".to_string(),
            logo_size: "100".to_string(),
            button_text: "Login".to_string(),
            message: "Click to access private documentation hosted by scalar.com".to_string(),
            title: "Private Docs".to_string(),
            main_color: "#2a2f45".to_string(),
            main_background: "#f6f6f6".to_string(),
            card_color: "#2a2f45".to_string(),
            card_background: "#fff".to_string(),
            button_color: "#fff".to_string(),
            button_background: "#0f0f0f".to_string(),
        },
        page: LoginPortalPage {
            title: "Scalar Private Docs".to_string(),
            description: "Login to access your documentation".to_string(),
            head: "".to_string(),
            script: "".to_string(),
            theme: "".to_string(),
            company_name: "".to_string(),
            logo: "".to_string(),
            logo_url: "".to_string(),
            favicon: "".to_string(),
            terms_link: "".to_string(),
            privacy_link: "".to_string(),
            form_title: "Scalar Private Docs".to_string(),
            form_description: "Login to access your documentation".to_string(),
            form_image: "".to_string(),
        },
    })
    .send()
    .await?;
```

### List all portals

List all login portals for the current team.

| Direction | Type |
| --- | --- |
| Response | [`Vec<LoginPortal>`](./src/models/login_portals.rs) |

```rust
let response = client.login_portals().list().send().await?;
```

## `AccessGroups`

Access Groups

### Create an access group

Create a group for the current team. Requires docs edit permission and the access groups billing feature. Domains are exact email domains, without wildcards or implicit subdomain matching.

| Direction | Type |
| --- | --- |
| Request | [`AccessGroupsCreateBody`](./src/models/access_groups.rs) |
| Response | [`AccessGroupsCreateResponse`](./src/models/access_groups.rs) |

```rust
let response = client
    .access_groups()
    .create(AccessGroupsCreateBody {
        name: None,
        slug: None,
        allowed_domains: None,
    })
    .send()
    .await?;
```

### Get an access group

Get a group and its email and domain allowlists by slug.

| Direction | Type |
| --- | --- |
| Response | [`AccessGroupsRetrieveResponse`](./src/models/access_groups.rs) |

```rust
let response = client.access_groups().retrieve("acme-api").send().await?;
```

### Update an access group

Update group metadata. Requires docs edit permission. After changing the slug, use the new slug in subsequent requests.

| Direction | Type |
| --- | --- |
| Request | [`AccessGroupsUpdateBody`](./src/models/access_groups.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .access_groups()
    .update("acme-api", AccessGroupsUpdateBody { name: None, slug: None })
    .send()
    .await?;
```

### Delete an access group

Delete a group and remove its project assignments. Requires docs edit permission.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.access_groups().delete("acme-api").send().await?;
```

### `AccessGroups Domains`

Access Groups

#### Add an allowed email domain

Allow an exact email domain in a group. Requires docs edit permission. A group supports up to 1000 domains.

| Direction | Type |
| --- | --- |
| Request | [`DomainsCreateBody`](./src/models/domains.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .access_groups()
    .domains()
    .create(
        "acme-api",
        DomainsCreateBody {
            domain: "example.com".to_string(),
        },
    )
    .send()
    .await?;
```

#### Remove an allowed email domain

Remove an exact email domain from a group. Requires docs edit permission. Other allowed domains and emails are preserved.

| Direction | Type |
| --- | --- |
| Request | [`DomainsDeleteBody`](./src/models/domains.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .access_groups()
    .domains()
    .delete(
        "acme-api",
        DomainsDeleteBody {
            domain: "example.com".to_string(),
        },
    )
    .send()
    .await?;
```

## `Rules`

Rules

### List all rules

List all rulesets in a namespace.

| Direction | Type |
| --- | --- |
| Response | [`Vec<Rule>`](./src/models/rules.rs) |

```rust
let response = client.rules().list_rulesets("acme").send().await?;
```

### Create a rule

Create a rule in a namespace.

| Direction | Type |
| --- | --- |
| Request | [`RulesCreateRulesetBody`](./src/models/rules.rs) |
| Response | [`Uid`](./src/models/shared.rs) |

```rust
let response = client
    .rules()
    .create_ruleset(
        "acme",
        RulesCreateRulesetBody {
            title: "Acme API Rules".to_string(),
            description: None,
            slug: "acme-rules".to_string(),
            is_private: None,
            document: "extends: [\"spectral:oas\"]\nrules:\n  info-contact: warn\n".to_string(),
        },
    )
    .send()
    .await?;
```

### Update rule metadata

Update rule metadata by slug.

| Direction | Type |
| --- | --- |
| Request | [`RulesUpdateRulesetBody`](./src/models/rules.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .rules()
    .update_ruleset(
        "acme",
        "acme-rules",
        RulesUpdateRulesetBody {
            namespace: None,
            slug: None,
            title: None,
            description: None,
            is_private: None,
        },
    )
    .send()
    .await?;
```

### Delete a rule

Delete a rule by slug.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.rules().delete_ruleset("acme", "acme-rules").send().await?;
```

### Get a rule

Get a rule document by slug.

| Direction | Type |
| --- | --- |
| Response | `bytes::Bytes` |

```rust
let response = client
    .rules()
    .retrieve_ruleset_document("acme", "acme-rules")
    .send()
    .await?;
```

### Add rule access group

Grant an access group to a rule.

| Direction | Type |
| --- | --- |
| Request | [`AccessGroup`](./src/models/registry.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .rules()
    .create_ruleset_access_group(
        "acme",
        "acme-rules",
        AccessGroup {
            access_group_slug: "acme-api".to_string(),
        },
    )
    .send()
    .await?;
```

### Remove rule access group

Remove an access group from a rule.

| Direction | Type |
| --- | --- |
| Request | [`AccessGroup`](./src/models/registry.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .rules()
    .delete_ruleset_access_group(
        "acme",
        "acme-rules",
        AccessGroup {
            access_group_slug: "acme-api".to_string(),
        },
    )
    .send()
    .await?;
```

## `Themes`

Themes

### List all themes

List all team themes.

| Direction | Type |
| --- | --- |
| Response | [`Vec<Theme>`](./src/models/themes.rs) |

```rust
let response = client.themes().list().send().await?;
```

### Create a theme

Create a team theme.

| Direction | Type |
| --- | --- |
| Request | [`ThemesCreateBody`](./src/models/themes.rs) |
| Response | [`Uid`](./src/models/shared.rs) |

```rust
let response = client
    .themes()
    .create(ThemesCreateBody {
        name: "Acme Theme".to_string(),
        description: None,
        slug: "acme-theme".to_string(),
        document: ":root { --scalar-color-1: #1f2937; }".to_string(),
    })
    .send()
    .await?;
```

### Update theme metadata

Update theme metadata.

| Direction | Type |
| --- | --- |
| Request | [`ThemesUpdateBody`](./src/models/themes.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .themes()
    .update(
        "acme-theme",
        ThemesUpdateBody {
            name: None,
            description: None,
        },
    )
    .send()
    .await?;
```

### Update theme document

Replace the theme document.

| Direction | Type |
| --- | --- |
| Request | [`ThemesReplaceDocumentBody`](./src/models/themes.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .themes()
    .replace_document(
        "acme-theme",
        ThemesReplaceDocumentBody {
            document: ":root { --scalar-color-1: #1f2937; }".to_string(),
        },
    )
    .send()
    .await?;
```

### Delete a theme

Delete a theme by slug.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.themes().delete("acme-theme").send().await?;
```

### Get a theme

Get the theme document by slug.

| Direction | Type |
| --- | --- |
| Response | `bytes::Bytes` |

```rust
let response = client.themes().retrieve("acme-theme").send().await?;
```

## `Teams`

Teams

### List teams

List all available teams

| Direction | Type |
| --- | --- |
| Response | [`Vec<Team>`](./src/models/teams.rs) |

```rust
let response = client.teams().list().send().await?;
```

### `Teams Members`

Teams

#### List team members

List the members of the current team, along with the invites still outstanding.

| Direction | Type |
| --- | --- |
| Response | [`MembersListResponse`](./src/models/members.rs) |

```rust
let response = client.teams().members().list().send().await?;
```

#### Change a member role

Change what a member of the current team is allowed to do.

| Direction | Type |
| --- | --- |
| Request | [`MembersUpdateBody`](./src/models/members.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .teams()
    .members()
    .update("UakgbKJ5m9gl0JDMbcJqL", MembersUpdateBody { role: Role::Owner })
    .send()
    .await?;
```

#### Remove a member

Remove someone from the current team.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.teams().members().delete("UakgbKJ5m9gl0JDMbcJqL").send().await?;
```

### `Teams Invites`

Teams

#### Invite a member

Invite someone to the current team by email.

| Direction | Type |
| --- | --- |
| Request | [`InvitesMemberBody`](./src/models/invites.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .teams()
    .invites()
    .member(InvitesMemberBody {
        email: "alex@example.com".to_string(),
        role: Role::Owner,
    })
    .send()
    .await?;
```

#### Resend an invite

Send the invite email again.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.teams().invites().resend("UakgbKJ5m9gl0JDMbcJqL").send().await?;
```

#### Cancel an invite

Withdraw an invite that has not been accepted.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.teams().invites().cancel("UakgbKJ5m9gl0JDMbcJqL").send().await?;
```

## `ScalarDocs`

Scalar Docs

### List all projects

List all guide projects.

| Direction | Type |
| --- | --- |
| Response | [`Vec<GithubProject>`](./src/models/scalar_docs.rs) |

```rust
let response = client.scalar_docs().list_guides().send().await?;
```

### Create a project

Create a guide project.

| Direction | Type |
| --- | --- |
| Request | [`ScalarDocsCreateGuideBody`](./src/models/scalar_docs.rs) |
| Response | [`ScalarDocsCreateGuideResponse`](./src/models/scalar_docs.rs) |

```rust
let response = client
    .scalar_docs()
    .create_guide(ScalarDocsCreateGuideBody {
        name: "Acme Documentation".to_string(),
        slug: None,
        is_private: false,
        allowed_users: vec![],
        allowed_domains: vec![],
    })
    .send()
    .await?;
```

### Publish a project

Start a new publish process.

| Direction | Type |
| --- | --- |
| Response | [`ScalarDocsPublishGuideResponse`](./src/models/scalar_docs.rs) |

```rust
let response = client.scalar_docs().publish_guide("acme-docs").send().await?;
```

### List all docs projects

List every docs project on the team.

| Direction | Type |
| --- | --- |
| Response | [`ScalarDocsListProjectsResponse`](./src/models/scalar_docs.rs) |

```rust
let response = client.scalar_docs().list_projects().send().await?;
```

### Create a docs project

Create a docs project. Omit `provider` to have Scalar host the repository.

| Direction | Type |
| --- | --- |
| Request | [`ScalarDocsCreateProjectBody`](./src/models/scalar_docs.rs) |
| Response | [`DocsProject`](./src/models/scalar_docs.rs) |

```rust
let response = client
    .scalar_docs()
    .create_project(ScalarDocsCreateProjectBody {
        name: "Acme Documentation".to_string(),
        slug: None,
        is_private: None,
        blank: None,
        provider: ScalarDocsCreateProjectBodyProvider::Forgejo,
        github_repository: None,
        bitbucket_repository: None,
    })
    .send()
    .await?;
```

### Get a docs project

Get a single docs project by its slug.

| Direction | Type |
| --- | --- |
| Response | [`DocsProject`](./src/models/scalar_docs.rs) |

```rust
let response = client.scalar_docs().retrieve_project("acme-docs").send().await?;
```

### Update a docs project

Update project settings. Set `isPrivate` with `accessGroups` to put the site behind a login.

| Direction | Type |
| --- | --- |
| Request | [`ScalarDocsUpdateProjectBody`](./src/models/scalar_docs.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .scalar_docs()
    .update_project(
        "acme-docs",
        ScalarDocsUpdateProjectBody {
            name: None,
            is_private: None,
            access_groups: None,
            login_portal_uid: None,
            active_theme_id: None,
            agent_enabled: None,
            analytics_enabled: None,
        },
    )
    .send()
    .await?;
```

### Delete a docs project

Delete a docs project, its deploys, its publish records and its cached builds.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.scalar_docs().delete_project("acme-docs").send().await?;
```

### Publish a docs project

Start a build and deploy. The returned `publishUid` identifies the publish record.

| Direction | Type |
| --- | --- |
| Request | [`ScalarDocsPublishProjectBody`](./src/models/scalar_docs.rs) |
| Response | [`ScalarDocsPublishProjectResponse`](./src/models/scalar_docs.rs) |

```rust
let response = client
    .scalar_docs()
    .publish_project(
        "acme-docs",
        ScalarDocsPublishProjectBody {
            commit_sha: None,
            preview: None,
            config_path: None,
        },
    )
    .send()
    .await?;
```

### Read the site config

Read `scalar.config.json` straight from the project repository, without cloning it. `baseToken` is the compare-and-swap handle for a later write.

| Direction | Type |
| --- | --- |
| Response | [`ScalarDocsListProjectConfigResponse`](./src/models/scalar_docs.rs) |

```rust
let response = client.scalar_docs().list_project_config("acme-docs").send().await?;
```

### Write the site config

Commit `scalar.config.json` straight to the project repository. Pass the `baseToken` from the read this edit was based on; a conflict means the file moved underneath it.

| Direction | Type |
| --- | --- |
| Request | [`ScalarDocsUpdateProjectConfigBody`](./src/models/scalar_docs.rs) |
| Response | [`ScalarDocsUpdateProjectConfigResponse`](./src/models/scalar_docs.rs) |

```rust
let response = client
    .scalar_docs()
    .update_project_config(
        "acme-docs",
        ScalarDocsUpdateProjectConfigBody {
            content: "{\"name\":\"Acme Documentation\"}".to_string(),
            r#ref: None,
            base_token: None,
            message: None,
            path: None,
        },
    )
    .send()
    .await?;
```

### Get the site domains

The domains the project serves on — the Scalar-hosted one and the custom one, when set.

| Direction | Type |
| --- | --- |
| Response | [`ScalarDocsListProjectDomainResponse`](./src/models/scalar_docs.rs) |

```rust
let response = client.scalar_docs().list_project_domain("acme-docs").send().await?;
```

### Check domain DNS

Whether the project custom domain points at Scalar yet. `expected` is the CNAME record to create; `found` is what resolves today. A project with no custom domain reports `verified` with no expected record, because Scalar serves its own subdomain directly.

| Direction | Type |
| --- | --- |
| Response | [`ScalarDocsListProjectDomainStatusResponse`](./src/models/scalar_docs.rs) |

```rust
let response = client
    .scalar_docs()
    .list_project_domain_status("acme-docs")
    .send()
    .await?;
```

## `Namespaces`

Namespaces

### List namespaces

Get all namespaces for the current team

| Direction | Type |
| --- | --- |
| Response | `Vec<String>` |

```rust
let response = client.namespaces().list().send().await?;
```

## `Authentication`

Authentication

### Exchange token

Exchange an API key for an access token.

| Direction | Type |
| --- | --- |
| Request | [`AuthenticationExchangePersonalTokenBody`](./src/models/authentication.rs) |
| Response | [`AuthenticationExchangePersonalTokenResponse`](./src/models/authentication.rs) |

```rust
let response = client
    .authentication()
    .exchange_personal_token(AuthenticationExchangePersonalTokenBody {
        personal_token: "scalar_example_personal_token".to_string(),
    })
    .send()
    .await?;
```

### Get current user

Get the authenticated user, including their available teams and theme.

| Direction | Type |
| --- | --- |
| Response | [`User`](./src/models/authentication.rs) |

```rust
let response = client.authentication().list_current_user().send().await?;
```

## `Sdks`

SDKs

### List all SDKs

List every SDK on the team.

| Direction | Type |
| --- | --- |
| Response | [`SdksListResponse`](./src/models/sdks.rs) |

```rust
let response = client.sdks().list().send().await?;
```

### Create an SDK

Create an SDK from an API document, targeting one or more languages.

| Direction | Type |
| --- | --- |
| Request | [`SdksCreateBody`](./src/models/sdks.rs) |
| Response | [`Uid`](./src/models/shared.rs) |

```rust
let response = client
    .sdks()
    .create(SdksCreateBody {
        api_uid: "UakgbKJ5m9gl0JDMbcJqL".to_string(),
        languages: vec![SdksCreateBodyLanguage::Typescript],
        title: None,
        slug: None,
        class_name: None,
        config: None,
    })
    .send()
    .await?;
```

### Get an SDK

Get a single SDK by its uid.

| Direction | Type |
| --- | --- |
| Response | [`Sdk`](./src/models/sdks.rs) |

```rust
let response = client.sdks().retrieve("UakgbKJ5m9gl0JDMbcJqL").send().await?;
```

### Update an SDK

Update SDK metadata, its linked API, or its config.

| Direction | Type |
| --- | --- |
| Request | [`SdksUpdateBody`](./src/models/sdks.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .sdks()
    .update(
        "UakgbKJ5m9gl0JDMbcJqL",
        SdksUpdateBody {
            title: None,
            slug: None,
            is_private: None,
            config: None,
            api_uid: None,
            api_version: None,
        },
    )
    .send()
    .await?;
```

### Delete an SDK

Delete an SDK and every version it holds.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.sdks().delete("UakgbKJ5m9gl0JDMbcJqL").send().await?;
```

### Build an SDK

Start a build. Omit `version` to build the current work — the open draft, else the latest version — and the resolved version comes back in the response.

| Direction | Type |
| --- | --- |
| Request | [`SdksBuildBody`](./src/models/sdks.rs) |
| Response | [`Option<SdksBuildResponse>`](./src/models/sdks.rs) |

```rust
let response = client
    .sdks()
    .build(
        "UakgbKJ5m9gl0JDMbcJqL",
        SdksBuildBody {
            version: None,
            languages: None,
        },
    )
    .send()
    .await?;
```

### `Sdks Versions`

SDKs

#### Create an SDK version

Create a new SDK version against a specific API version.

| Direction | Type |
| --- | --- |
| Request | [`VersionsCreateBody`](./src/models/versions.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .sdks()
    .versions()
    .create(
        "UakgbKJ5m9gl0JDMbcJqL",
        VersionsCreateBody {
            version: "1.2.0".to_string(),
            api_version: "1.2.0".to_string(),
        },
    )
    .send()
    .await?;
```

#### Delete an SDK version

Permanently delete one version of an SDK.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client
    .sdks()
    .versions()
    .delete("UakgbKJ5m9gl0JDMbcJqL", "1.2.0")
    .send()
    .await?;
```

### `Sdks Repositories`

SDKs

#### Link a repository

Link one language target to a GitHub repository, so builds sync there.

| Direction | Type |
| --- | --- |
| Request | [`RepositoriesLinkBody`](./src/models/repositories.rs) |
| Response | [`Option<RepositoriesLinkResponse>`](./src/models/repositories.rs) |

```rust
let response = client
    .sdks()
    .repositories()
    .link(
        "UakgbKJ5m9gl0JDMbcJqL",
        RepositoriesLinkBody {
            language: RepositoriesLinkBodyLanguage::Typescript,
            repository_id: 123456789,
            base_branch: "main".to_string(),
            prerelease_type: None,
        },
    )
    .send()
    .await?;
```

#### Unlink a repository

Unlink one language target from its repository.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client
    .sdks()
    .repositories()
    .unlink("UakgbKJ5m9gl0JDMbcJqL", "typescript".to_string())
    .send()
    .await?;
```

#### Update publishing settings

Toggle publish-on-merge and the release settings for a linked target.

| Direction | Type |
| --- | --- |
| Request | [`RepositoriesUpdatePublishingBody`](./src/models/repositories.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .sdks()
    .repositories()
    .update_publishing(
        "UakgbKJ5m9gl0JDMbcJqL",
        "typescript".to_string(),
        RepositoriesUpdatePublishingBody {
            publish_on_merge: true,
            auth_method: None,
            access: None,
            tag: None,
        },
    )
    .send()
    .await?;
```

## `Mcp`

### `Mcp Servers`

MCP

#### List all MCP servers

List every MCP server on the team.

| Direction | Type |
| --- | --- |
| Response | [`Vec<McpServer>`](./src/models/servers.rs) |

```rust
let response = client.mcp().servers().list().send().await?;
```

#### Create an MCP server

Create an MCP server over one or more API document versions. The response carries the server and its first installation.

| Direction | Type |
| --- | --- |
| Request | [`ServersCreateBody`](./src/models/servers.rs) |
| Response | [`ServersCreateResponse`](./src/models/servers.rs) |

```rust
let response = client
    .mcp()
    .servers()
    .create(ServersCreateBody {
        name: "Acme MCP".to_string(),
        slug: None,
        version_uids: None,
        project_uids: None,
    })
    .send()
    .await?;
```

#### Get an MCP server

Get a single MCP server by its id.

| Direction | Type |
| --- | --- |
| Response | [`McpServer`](./src/models/servers.rs) |

```rust
let response = client.mcp().servers().retrieve("42").send().await?;
```

#### Update an MCP server

Update MCP server metadata and which tools it exposes.

| Direction | Type |
| --- | --- |
| Request | [`ServersUpdateBody`](./src/models/servers.rs) |
| Response | [`McpServer`](./src/models/servers.rs) |

```rust
let response = client
    .mcp()
    .servers()
    .update(
        "42",
        ServersUpdateBody {
            name: None,
            slug: None,
            auto_add_operations: None,
            operations: None,
            docs_pages: None,
        },
    )
    .send()
    .await?;
```

#### Delete an MCP server

Delete an MCP server and every installation it serves.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.mcp().servers().delete("42").send().await?;
```

#### `Mcp Servers Installations`

MCP

##### List installations

List the installations of an MCP server. An installation is what an MCP client connects to.

| Direction | Type |
| --- | --- |
| Response | [`Vec<McpInstallationListItem>`](./src/models/installations.rs) |

```rust
let response = client.mcp().servers().installations().list("42").send().await?;
```

##### Create an installation

Create an installation of an MCP server. `documentAuth` holds the credentials the server presents to the upstream API and is never returned.

| Direction | Type |
| --- | --- |
| Request | [`InstallationsCreateBody`](./src/models/installations.rs) |
| Response | [`McpInstallation`](./src/models/servers.rs) |

```rust
let response = client
    .mcp()
    .servers()
    .installations()
    .create(
        "42",
        InstallationsCreateBody {
            name: "Acme MCP".to_string(),
            slug: None,
            document_auth: std::collections::HashMap::from([]),
        },
    )
    .send()
    .await?;
```

##### Get an installation

Get a single installation of an MCP server.

| Direction | Type |
| --- | --- |
| Response | [`McpInstallation`](./src/models/servers.rs) |

```rust
let response = client
    .mcp()
    .servers()
    .installations()
    .retrieve("42", "84")
    .send()
    .await?;
```

##### Update an installation

Update an installation. Set `isPrivate` and add access groups to put it behind a login.

| Direction | Type |
| --- | --- |
| Request | [`InstallationsUpdateBody`](./src/models/installations.rs) |
| Response | [`McpInstallation`](./src/models/servers.rs) |

```rust
let response = client
    .mcp()
    .servers()
    .installations()
    .update(
        "42",
        "84",
        InstallationsUpdateBody {
            name: None,
            slug: None,
            is_private: None,
            login_portal_uid: None,
            document_auth: None,
            mcp_version: None,
        },
    )
    .send()
    .await?;
```

##### Delete an installation

Delete an installation of an MCP server.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.mcp().servers().installations().delete("42", "84").send().await?;
```

##### Add an access group

Let an access group reach a private installation.

| Direction | Type |
| --- | --- |
| Request | [`InstallationsCreateAccessGroupBody`](./src/models/installations.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .mcp()
    .servers()
    .installations()
    .create_access_group(
        "42",
        "84",
        InstallationsCreateAccessGroupBody {
            access_group_uid: "UakgbKJ5m9gl0JDMbcJqL".to_string(),
        },
    )
    .send()
    .await?;
```

##### Remove an access group

Stop an access group reaching a private installation.

| Direction | Type |
| --- | --- |
| Request | [`InstallationsDeleteAccessGroupBody`](./src/models/installations.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .mcp()
    .servers()
    .installations()
    .delete_access_group(
        "42",
        "84",
        InstallationsDeleteAccessGroupBody {
            access_group_uid: "UakgbKJ5m9gl0JDMbcJqL".to_string(),
        },
    )
    .send()
    .await?;
```

## `OAuth`

OAuth

### Start an OAuth authorization

Authorization endpoint (RFC 6749 §4.1.1 with PKCE, RFC 7636). Validates the request and sends the user to the Scalar dashboard to approve it; the user returns to `redirect_uri` with a `code` to exchange at the token endpoint. Only `response_type=code` with `code_challenge_method=S256` is supported.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.o_auth().oauth_authorize().send().await?;
```

### Exchange a code or refresh token

Token endpoint (RFC 6749 §4.1.3 and §6). Accepts `application/x-www-form-urlencoded`. Confidential clients authenticate with HTTP Basic or `client_secret` in the body; public clients send `client_id` alone. The `authorization_code` grant needs `code`, `redirect_uri` and `code_verifier`; the `refresh_token` grant needs `refresh_token` and may narrow `scope`.

| Direction | Type |
| --- | --- |
| Request | [`OauthTokenRequest`](./src/models/o_auth.rs) |
| Response | [`OAuthOauthTokenResponse`](./src/models/o_auth.rs) |

```rust
let response = client
    .o_auth()
    .oauth_token(OauthTokenRequest {
        grant_type: "".to_string(),
        client_id: None,
        client_secret: None,
        code: None,
        redirect_uri: None,
        code_verifier: None,
        refresh_token: None,
        scope: None,
    })
    .send()
    .await?;
```

### Revoke a refresh token

Revocation endpoint (RFC 7009). Revokes the refresh token and every token issued alongside it. The client authenticates as it does at the token endpoint. Responds 200 whether or not the token was live, as the RFC requires.

| Direction | Type |
| --- | --- |
| Request | [`OauthRevokeRequest`](./src/models/o_auth.rs) |
| Response | [`Option<OauthError>`](./src/models/o_auth.rs) |

```rust
let response = client
    .o_auth()
    .oauth_revoke(OauthRevokeRequest {
        token: "".to_string(),
        token_type_hint: None,
        client_id: None,
        client_secret: None,
    })
    .send()
    .await?;
```

### Authorization server metadata

Discovery document for OAuth clients (RFC 8414): where the endpoints are and what they support.

| Direction | Type |
| --- | --- |
| Response | [`OauthAuthorizationServerMetadata`](./src/models/o_auth.rs) |

```rust
let response = client.o_auth().oauth_authorization_server_metadata().send().await?;
```
