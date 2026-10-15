# Contributing

Thank you for helping improve Replica Audio Player. Contributions should keep the project reliable, maintainable, accessible, and safe for Linux users.

## Before opening a change

1. Check existing issues and pull requests to avoid duplicated work.
2. For large changes, open an issue first to discuss scope and design.
3. Never include credentials, personal data, private music files, local databases, or machine-specific paths.
4. For security issues, follow [SECURITY.md](SECURITY.md) and do not open a public issue.

## Development prerequisites

The application targets Linux and uses Rust, GTK 4, Libadwaita, SQLite, and ALSA development libraries.

On Ubuntu/Debian:

```bash
sudo apt-get update
sudo apt-get install build-essential pkg-config libgtk-4-dev libadwaita-1-dev libsqlite3-dev libasound2-dev
```

Install the stable Rust toolchain using the official instructions at https://rustup.rs/.

## Local validation

Run these checks before submitting a pull request:

```bash
cargo fmt --all -- --check
cargo clippy --all-targets --all-features -- -D warnings
cargo audit
cargo test --all-targets --all-features --locked
```

Install the audit tool if needed:

```bash
cargo install cargo-audit --locked
```

If a command cannot run because implementation or test targets are not yet present, explain that clearly in the pull request rather than claiming it passed.

## Pull requests

- Keep changes focused and describe the motivation, implementation, and user-visible impact.
- Include tests for behavior changes where practical.
- Update documentation when commands, dependencies, or behavior change.
- Explain any new permissions, network access, subprocess execution, or handling of local files.
- Do not commit generated build output or lockfile changes unrelated to the dependency update.
- Include screenshots for material UI changes when useful.
- Confirm that no secrets or sensitive user data are included.

Use Conventional Commit-style messages where practical, for example `feat: add library scanning`, `fix: handle missing audio metadata`, or `docs: clarify Linux dependencies`.

All contributions are subject to review. Submitting a pull request does not guarantee acceptance.
