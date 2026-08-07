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
- [`ScalarDocs`](#scalardocs)
  - [List all projects](#list-all-projects)
  - [Create a project](#create-a-project)
  - [Publish a project](#publish-a-project)
- [`Namespaces`](#namespaces)
  - [List namespaces](#list-namespaces)
- [`Authentication`](#authentication)
  - [Exchange token](#exchange-token)
  - [Get current user](#get-current-user)

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

### List all API Documents

List all API documents across every namespace the caller can access.

| Direction | Type |
| --- | --- |
| Response | [`Vec<ApiDocument>`](./src/models.rs) |

```rust
let response = client.registry().list_all_api_documents().send().await?;
```

### List API Documents in a namespace

List API documents in a namespace.

| Direction | Type |
| --- | --- |
| Response | [`Vec<ApiDocument>`](./src/models.rs) |

```rust
let response = client.registry().list_api_documents("example").send().await?;
```

### Create API Document

Create an API document.

| Direction | Type |
| --- | --- |
| Request | [`RegistryCreateApiDocumentBody`](./src/models.rs) |
| Response | [`RegistryCreateApiDocumentResponse`](./src/models.rs) |

```rust
let response = client
    .registry()
    .create_api_document(
        "example",
        RegistryCreateApiDocumentBody {
            title: "".to_string(),
            description: None,
            version: "x".to_string(),
            slug: "".to_string(),
            ruleset: None,
            is_private: None,
            document: "".to_string(),
        },
    )
    .send()
    .await?;
```

### Update API Document metadata

Update metadata for an API document.

| Direction | Type |
| --- | --- |
| Request | [`RegistryUpdateApiDocumentBody`](./src/models.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .registry()
    .update_api_document(
        "example",
        "example",
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
let response = client
    .registry()
    .delete_api_document("example", "example")
    .send()
    .await?;
```

### Get API Document

Get a specific API document version.

| Direction | Type |
| --- | --- |
| Response | `bytes::Bytes` |

```rust
let response = client
    .registry()
    .retrieve_api_document_version("example", "example", "example")
    .send()
    .await?;
```

### Update API Document version

Update the registry file content for an API document version.

| Direction | Type |
| --- | --- |
| Request | [`RegistryUpdateApiDocumentVersionBody`](./src/models.rs) |
| Response | [`RegistryUpdateApiDocumentVersionResponse`](./src/models.rs) |

```rust
let response = client
    .registry()
    .update_api_document_version(
        "example",
        "example",
        "example",
        RegistryUpdateApiDocumentVersionBody {
            document: "".to_string(),
            last_known_version_sha: None,
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
    .delete_api_document_version("example", "example", "example")
    .send()
    .await?;
```

### Get API Document version metadata

Get metadata (uid, content shas, version sha, tags) for a specific API document version.

| Direction | Type |
| --- | --- |
| Response | [`ManagedDocVersion`](./src/models.rs) |

```rust
let response = client
    .registry()
    .list_api_document_version_metadata("example", "example", "example")
    .send()
    .await?;
```

### Create API Document version

Create a new API document version.

| Direction | Type |
| --- | --- |
| Request | [`RegistryCreateApiDocumentVersionBody`](./src/models.rs) |
| Response | [`ManagedDocVersion`](./src/models.rs) |

```rust
let response = client
    .registry()
    .create_api_document_version(
        "example",
        "example",
        RegistryCreateApiDocumentVersionBody {
            version: "x".to_string(),
            document: "".to_string(),
            force: None,
            last_known_version_sha: None,
        },
    )
    .send()
    .await?;
```

### Add access group

Add an access group to an API document.

| Direction | Type |
| --- | --- |
| Request | [`AccessGroup`](./src/models.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .registry()
    .create_api_document_access_group(
        "example",
        "example",
        AccessGroup {
            access_group_slug: "xxx".to_string(),
        },
    )
    .send()
    .await?;
```

### Remove access group

Remove an access group from an API document.

| Direction | Type |
| --- | --- |
| Request | [`AccessGroup`](./src/models.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .registry()
    .delete_api_document_access_group(
        "example",
        "example",
        AccessGroup {
            access_group_slug: "xxx".to_string(),
        },
    )
    .send()
    .await?;
```

## `Schemas`

### List all shared components

List schemas in a namespace.

| Direction | Type |
| --- | --- |
| Response | [`Vec<Schema>`](./src/models.rs) |

```rust
let response = client.schemas().list("example").send().await?;
```

### Create a shared component

Create a schema in a namespace.

| Direction | Type |
| --- | --- |
| Request | [`SchemasCreateBody`](./src/models.rs) |
| Response | [`Uid`](./src/models.rs) |

```rust
let response = client
    .schemas()
    .create(
        "example",
        SchemasCreateBody {
            title: "".to_string(),
            description: None,
            version: "x".to_string(),
            slug: "".to_string(),
            is_private: None,
            document: "".to_string(),
        },
    )
    .send()
    .await?;
```

### Update shared component metadata

Update schema metadata.

| Direction | Type |
| --- | --- |
| Request | [`SchemasUpdateBody`](./src/models.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .schemas()
    .update(
        "example",
        "example",
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
let response = client.schemas().delete("example", "example").send().await?;
```

### `Schemas Version`

#### Get a shared component document

Get a specific schema version document.

| Direction | Type |
| --- | --- |
| Response | `bytes::Bytes` |

```rust
let response = client
    .schemas()
    .version()
    .retrieve_schema("example", "example", "example")
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
    .delete_schema("example", "example", "example")
    .send()
    .await?;
```

#### Create a shared component version

Create a schema version.

| Direction | Type |
| --- | --- |
| Request | [`VersionCreateSchemaBody`](./src/models.rs) |
| Response | [`Uid`](./src/models.rs) |

```rust
let response = client
    .schemas()
    .version()
    .create_schema(
        "example",
        "example",
        VersionCreateSchemaBody {
            version: "x".to_string(),
            document: "".to_string(),
        },
    )
    .send()
    .await?;
```

### `Schemas AccessGroup`

#### Add shared component access group

Add an access group to a schema.

| Direction | Type |
| --- | --- |
| Request | [`AccessGroup`](./src/models.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .schemas()
    .access_group()
    .create_schema(
        "example",
        "example",
        AccessGroup {
            access_group_slug: "xxx".to_string(),
        },
    )
    .send()
    .await?;
```

#### Remove shared component access group

Remove an access group from a schema.

| Direction | Type |
| --- | --- |
| Request | [`AccessGroup`](./src/models.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .schemas()
    .access_group()
    .delete_schema(
        "example",
        "example",
        AccessGroup {
            access_group_slug: "xxx".to_string(),
        },
    )
    .send()
    .await?;
```

## `LoginPortals`

### Get a login portal

Get a login portal by slug.

| Direction | Type |
| --- | --- |
| Response | [`LoginPortalsRetrieveResponse`](./src/models.rs) |

```rust
let response = client.login_portals().retrieve("example").send().await?;
```

### Update portal metadata

Update metadata for a login portal.

| Direction | Type |
| --- | --- |
| Request | [`LoginPortalsUpdateBody`](./src/models.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .login_portals()
    .update("example", LoginPortalsUpdateBody { title: None })
    .send()
    .await?;
```

### Delete a login portal

Delete a login portal.

| Direction | Type |
| --- | --- |
| Response | `serde_json::Value` |

```rust
let response = client.login_portals().delete("example").send().await?;
```

### Create a portal

Create a login portal for the current team.

| Direction | Type |
| --- | --- |
| Request | [`LoginPortalsCreateBody`](./src/models.rs) |
| Response | [`Uid`](./src/models.rs) |

```rust
let response = client
    .login_portals()
    .create(LoginPortalsCreateBody {
        title: "".to_string(),
        slug: "".to_string(),
        email: LoginPortalEmail {
            logo: "".to_string(),
            logo_size: "100".to_string(),
            button_text: "Login".to_string(),
            message: "Click to access private documentation hosted by scalar.com".to_string(),
            title: "Private Docs".to_string(),
            main_color: "#2a2f45".to_string(),
            main_background: "#f6f6f6".to_string(),
            card_color: "2a2f45".to_string(),
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
| Response | [`Vec<LoginPortal>`](./src/models.rs) |

```rust
let response = client.login_portals().list().send().await?;
```

## `Rules`

### List all rules

List all rulesets in a namespace.

| Direction | Type |
| --- | --- |
| Response | [`Vec<Rule>`](./src/models.rs) |

```rust
let response = client.rules().list_rulesets("example").send().await?;
```

### Create a rule

Create a rule in a namespace.

| Direction | Type |
| --- | --- |
| Request | [`RulesCreateRulesetBody`](./src/models.rs) |
| Response | [`Uid`](./src/models.rs) |

```rust
let response = client
    .rules()
    .create_ruleset(
        "example",
        RulesCreateRulesetBody {
            title: "".to_string(),
            description: None,
            slug: "".to_string(),
            is_private: None,
            document: "".to_string(),
        },
    )
    .send()
    .await?;
```

### Update rule metadata

Update rule metadata by slug.

| Direction | Type |
| --- | --- |
| Request | [`RulesUpdateRulesetBody`](./src/models.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .rules()
    .update_ruleset(
        "example",
        "example",
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
let response = client.rules().delete_ruleset("example", "example").send().await?;
```

### Get a rule

Get a rule document by slug.

| Direction | Type |
| --- | --- |
| Response | `bytes::Bytes` |

```rust
let response = client
    .rules()
    .retrieve_ruleset_document("example", "example")
    .send()
    .await?;
```

### Add rule access group

Grant an access group to a rule.

| Direction | Type |
| --- | --- |
| Request | [`AccessGroup`](./src/models.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .rules()
    .create_ruleset_access_group(
        "example",
        "example",
        AccessGroup {
            access_group_slug: "xxx".to_string(),
        },
    )
    .send()
    .await?;
```

### Remove rule access group

Remove an access group from a rule.

| Direction | Type |
| --- | --- |
| Request | [`AccessGroup`](./src/models.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .rules()
    .delete_ruleset_access_group(
        "example",
        "example",
        AccessGroup {
            access_group_slug: "xxx".to_string(),
        },
    )
    .send()
    .await?;
```

## `Themes`

### List all themes

List all team themes.

| Direction | Type |
| --- | --- |
| Response | [`Vec<Theme>`](./src/models.rs) |

```rust
let response = client.themes().list().send().await?;
```

### Create a theme

Create a team theme.

| Direction | Type |
| --- | --- |
| Request | [`ThemesCreateBody`](./src/models.rs) |
| Response | [`Uid`](./src/models.rs) |

```rust
let response = client
    .themes()
    .create(ThemesCreateBody {
        name: "".to_string(),
        description: None,
        slug: "".to_string(),
        document: "".to_string(),
    })
    .send()
    .await?;
```

### Update theme metadata

Update theme metadata.

| Direction | Type |
| --- | --- |
| Request | [`ThemesUpdateBody`](./src/models.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .themes()
    .update(
        "example",
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
| Request | [`ThemesReplaceDocumentBody`](./src/models.rs) |
| Response | `serde_json::Value` |

```rust
let response = client
    .themes()
    .replace_document(
        "example",
        ThemesReplaceDocumentBody {
            document: "".to_string(),
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
let response = client.themes().delete("example").send().await?;
```

### Get a theme

Get the theme document by slug.

| Direction | Type |
| --- | --- |
| Response | `bytes::Bytes` |

```rust
let response = client.themes().retrieve("example").send().await?;
```

## `Teams`

### List teams

List all available teams

| Direction | Type |
| --- | --- |
| Response | [`Vec<Team>`](./src/models.rs) |

```rust
let response = client.teams().list().send().await?;
```

## `ScalarDocs`

### List all projects

List all guide projects.

| Direction | Type |
| --- | --- |
| Response | [`Vec<GithubProject>`](./src/models.rs) |

```rust
let response = client.scalar_docs().list_guides().send().await?;
```

### Create a project

Create a guide project.

| Direction | Type |
| --- | --- |
| Request | [`ScalarDocsCreateGuideBody`](./src/models.rs) |
| Response | [`ScalarDocsCreateGuideResponse`](./src/models.rs) |

```rust
let response = client
    .scalar_docs()
    .create_guide(ScalarDocsCreateGuideBody {
        name: "".to_string(),
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
| Response | [`ScalarDocsPublishGuideResponse`](./src/models.rs) |

```rust
let response = client.scalar_docs().publish_guide("example").send().await?;
```

## `Namespaces`

### List namespaces

Get all namespaces for the current team

| Direction | Type |
| --- | --- |
| Response | `Vec<String>` |

```rust
let response = client.namespaces().list().send().await?;
```

## `Authentication`

### Exchange token

Exchange an API key for an access token.

| Direction | Type |
| --- | --- |
| Request | [`AuthenticationExchangePersonalTokenBody`](./src/models.rs) |
| Response | [`AuthenticationExchangePersonalTokenResponse`](./src/models.rs) |

```rust
let response = client
    .authentication()
    .exchange_personal_token(AuthenticationExchangePersonalTokenBody {
        personal_token: "".to_string(),
    })
    .send()
    .await?;
```

### Get current user

Get the authenticated user, including their available teams and theme.

| Direction | Type |
| --- | --- |
| Response | [`User`](./src/models.rs) |

```rust
let response = client.authentication().list_current_user().send().await?;
```
