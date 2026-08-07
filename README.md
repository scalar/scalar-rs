# Scalar API

This library provides convenient access to the Scalar API from asynchronous Rust.

The full API of this library can be found in [api.md](./api.md).

## Installation

```sh
cargo add scalar-rs
cargo add tokio --features full
```

## Usage

The client is asynchronous and built on `tokio` + `reqwest`. Construct it
with the builder, or read credentials from the environment:

```rust,no_run
use scalar_rs::Scalar;

async fn run() -> Result<(), Box<dyn std::error::Error>> {
    let client = Scalar::builder()
        .bearer_token("…")
        .build()?;

    // Or, reading credentials from the environment:
    let client = Scalar::from_env()?;
    let _ = client;
    Ok(())
}
```

Every operation returns a request builder; set optional parameters fluently
and finish with `.send().await`:

```rust,ignore
let response = client.registry().list_all_api_documents().send().await?;
```

## Authentication

Credentials can be set on the builder or read from the environment by
`from_env`:

- `bearer_token` — environment variable `SCALAR_BEARER_TOKEN`

## Error handling

Fallible operations return [`scalar_rs::Error`]. Match on the
result of `send().await` to distinguish API errors (with status and decoded
body) from transport and decoding failures:

```rust,ignore
use scalar_rs::Error;

match result {
    Ok(value) => { /* … */ }
    Err(Error::Api(api)) => eprintln!("status {}: {:?}", api.status, api.body),
    Err(other) => eprintln!("request failed: {other}"),
}
```

## API reference

See [`api.md`](./api.md) for the full list of resources and operations.
