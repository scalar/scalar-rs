# Changelog

All notable changes to `scalar-rs` are documented here. Release
tooling appends a section per released version below.

## Unreleased

- Initial generation of the `scalar-rs` SDK.
- Response-only models are marked `#[non_exhaustive]`, so new response
  fields can be added in future versions without a breaking release;
  request models stay literally constructible.
