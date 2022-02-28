# Evg Bonsai pot for rust.

This [evg-bonsai](https://github.com/dbradf/evg-bonsai) pot supports running
rust actions in evergreen.

## Usage

Example landscape file:
```yaml
bonsai:
  - source: github
    owner: dbradf
    repo: evg-bonsai-rust

pre:
  - bonsai: cargo:install rust
    params:
      rust_version: stable

tasks:
  - name: unit_tests
    commands:
    - bonsai: cargo:run
      params:
        target_dir: src
        cargo_command: test

  - name: format
    commands:
    - bonsai: cargo:run
      params:
        target_dir: src
        cargo_command: fmt --check

  - name: lint
    commands:
    - bonsai: cargo:run
      params:
        target_dir: src
        cargo_command: clippy
```
