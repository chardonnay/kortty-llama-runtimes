# korTTY llama.cpp runtimes

This repository contains immutable, platform-specific `llama-server` packages for [korTTY](https://github.com/chardonnay/korTTY). Packages are built by GitHub Actions from an exact korTTY source commit, verified against korTTY's pinned llama.cpp source archive, smoke-tested, and published with a cumulative Ed25519-signed index.

The repository contains native runtime binaries only. It never contains GGUF model weights, credentials, user data, or a general-purpose llama.cpp web interface.

## Stable channel

korTTY reads these assets from the latest non-draft release:

- `runtime-index-v1.json` — cumulative platform/backend package catalog and revocations
- `runtime-index-v1.sig` — Base64-encoded Ed25519 signature over the exact index bytes
- `llama-…-<platform>-<architecture>-<backend>.zip` — immutable runtime package

The MLX channel works the same way with `mlx-runtime-index-v1.json` / `mlx-runtime-index-v1.sig` and `mlx-…` packages (Apple Silicon macOS only). Every promotion of either channel creates a new immutable release marked latest that carries **both** signed indexes — the other channel's index is copied byte-for-byte from its newest release — so both channels resolve through `releases/latest`. The rolling `mlx-stable` pre-release is only kept as the legacy MLX pointer for older korTTY builds.

The signing private key is restricted to the `llama-runtime-signing` GitHub environment. korTTY embeds only the public verification key and rejects unsigned, modified, incompatible, or revoked packages.

Stable publication is a manually dispatched workflow. Regular promotions are limited to one per seven days; audited security and model-support updates may override that cadence.
