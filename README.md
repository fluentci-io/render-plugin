# Render Plugin

[![fluentci pipeline](https://shield.fluentci.io/x/render)](https://pkg.fluentci.io/render)
[![ci](https://github.com/fluentci-io/render-plugin/actions/workflows/ci.yml/badge.svg)](https://github.com/fluentci-io/render-plugin/actions/workflows/ci.yml)

This plugin sets up your CI/CD pipeline with a specific version of [Render](https://github.com/render-oss/render-cli).

## 🚀 Usage

Add the following command to your CI configuration file:

```bash
fluentci run --wasm render setup
```

## Functions

| Name     | Description                                        |
| -------- | -------------------------------------------------- |
| setup    | Install a specific version of render.             |

## Code Usage

Add `fluentci-pdk` crate to your `Cargo.toml`:

```toml
[dependencies]
fluentci-pdk = "0.2.1"
```

Use the following code to call the plugin:

```rust
use fluentci_pdk::dag;

// ...

dag().call("https://pkg.fluentci.io/render@v0.1.0?wasm=1", "setup", vec!["latest"])?;
```

## 📚 Examples

Github Actions:

```yaml
- name: Setup Fluent CI CLI
  uses: fluentci-io/setup-fluentci@v5
  with:
    wasm: true
    plugin: render
    args: |
      setup
- name: Show render version
  run: |
    type render
    render version
```
