# Replica Audio Player

[![CI](https://github.com/gustavormartins/Replica-audio-player/actions/workflows/ci.yml/badge.svg)](https://github.com/gustavormartins/Replica-audio-player/actions/workflows/ci.yml)
[![Security Policy](https://img.shields.io/badge/security-policy-blue)](SECURITY.md)
[![Platform](https://img.shields.io/badge/platform-Linux-informational)](#linux-prerequisites)
[![Language](https://img.shields.io/badge/language-Rust-orange)](https://www.rust-lang.org/)

A native Linux audio player project built with Rust and a GTK/Libadwaita interface. The goal is to develop a maintainable desktop application for managing and playing a user's local audio library.

> **Development status:** Early development. Features, build requirements, and architecture may change. Do not assume production readiness.

## Project goals

- A native desktop experience integrated with the Linux environment.
- A clear separation between interface, playback, metadata, and persistence.
- Local-first handling of the music library.
- Reproducible builds and automated quality checks.
- Security-conscious dependency and contribution practices.

This is an independent audio-player project. It does not include Spotify's branding, private APIs, or proprietary content.

## Linux prerequisites

On Ubuntu/Debian, install the native development packages:

```bash
sudo apt-get update
sudo apt-get install build-essential pkg-config libgtk-4-dev libadwaita-1-dev libsqlite3-dev libasound2-dev
```

Install the stable Rust toolchain from https://rustup.rs/.

Package names may differ by distribution. The dependencies above reflect the current CI environment and may be adjusted as the implementation evolves.

## Build and run

From the repository root:

```bash
cargo build --locked
cargo run
```

Run the quality checks:

```bash
cargo fmt --all -- --check
cargo clippy --all-targets --all-features -- -D warnings
cargo test --all-targets --all-features --locked
```

Run the dependency vulnerability audit (requires the `cargo-audit` tool):

```bash
cargo install cargo-audit --locked
cargo audit
```

These commands require a valid Rust project manifest and implemented targets. As the project is currently being bootstrapped, some build and test commands may not pass until the application code and `Cargo.toml` are added.

## Repository layout

The planned organization separates application entry points, UI, data models, persistence, and audio playback. Directories and modules will be added as implementation progresses.

```text
.github/
  workflows/
    ci.yml
  PULL_REQUEST_TEMPLATE.md
resources/
  icons/
  styles/
src/
  app.rs
  main.rs
  db/
  models/
  playback/
  ui/
tests/
docs/
.gitignore
CONTRIBUTING.md
README.md
SECURITY.md
```

## Security

Please read [SECURITY.md](SECURITY.md) before reporting a vulnerability. Do not disclose suspected vulnerabilities in public issues. Never commit credentials, tokens, private keys, local databases, or personal media.

The CI workflow checks formatting, runs Clippy with warnings denied, audits Rust dependencies, and runs tests when a Rust project is present.

## Contributing

Contributions are welcome after reviewing [CONTRIBUTING.md](CONTRIBUTING.md). Please keep pull requests focused, document meaningful changes, and report honestly which checks were run.

## License

No license has been selected yet. Until a license is added, do not assume that the repository's code is available for reuse, redistribution, or modification. A license should be chosen before inviting external reuse.
