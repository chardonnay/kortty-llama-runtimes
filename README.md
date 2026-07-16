# korTTY llama.cpp runtimes

This repository contains immutable, platform-specific `llama-server` packages for [korTTY](https://github.com/chardonnay/korTTY). Packages are built by GitHub Actions from an exact korTTY source commit, verified against korTTY's pinned llama.cpp source archive, smoke-tested, and published with a cumulative Ed25519-signed index.

The repository contains native runtime binaries only. It never contains GGUF model weights, credentials, user data, or a general-purpose llama.cpp web interface.

## Stable channel

korTTY reads these assets from the latest non-draft release:

- `runtime-index-v1.json` — cumulative platform/backend package catalog and revocations
- `runtime-index-v1.sig` — Base64-encoded Ed25519 signature over the exact index bytes
- `llama-…-<platform>-<architecture>-<backend>.zip` — immutable runtime package

The signing private key is restricted to the `llama-runtime-signing` GitHub environment. korTTY embeds only the public verification key and rejects unsigned, modified, incompatible, or revoked packages.

Stable publication is a manually dispatched workflow. Regular promotions are limited to one per seven days; audited security and model-support updates may override that cadence.
