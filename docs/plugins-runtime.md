# WASM Plugin Runtime (Experimental)

This document describes the current experimental plugin runtime for ZeroClaw.

## Scope

Current implementation supports:

- plugin manifest discovery from `[plugins].load_paths`
- plugin-declared tool registration into tool specs
- plugin-declared provider registration into provider factory resolution
- host-side WASM invocation bridge for tool/provider calls
- manifest fingerprint tracking scaffolding and optional runtime hot-reload controls

## Config

```toml
[plugins]
enabled = true
hot_reload = false
load_paths = ["plugins"]
limits = { invoke_timeout_ms = 2000, memory_limit_bytes = 67108864, max_concurrency = 8 }
allow = []
deny = []
```

Defaults are deny-by-default and disabled-by-default.
Execution limits are conservative and now exposed as config:

- `invoke_timeout_ms = 2000`
- `memory_limit_bytes = 67108864`
- `max_concurrency = 8`

Hot-reload behavior:

- `hot_reload = false`: manifests are loaded once at startup.
- `hot_reload = true`: manifests are reloaded when file fingerprints change.

## Manifest Files

The runtime scans each configured directory for:

- `*.plugin.toml`
- `*.plugin.json`

Minimal TOML example:

```toml
id = "demo"
version = "1.0.0"
module_path = "plugins/demo.wasm"
wit_packages = ["zeroclaw:tools@1.0.0", "zeroclaw:providers@1.0.0"]

[[tools]]
name = "demo_tool"
description = "Demo tool"

providers = ["demo-provider"]
```

## WIT Package Compatibility

Supported package majors:

- `zeroclaw:hooks@1.x`
- `zeroclaw:tools@1.x`
- `zeroclaw:providers@1.x`

Unknown packages or mismatched major versions are rejected during manifest load.

## WASM Host ABI (Current Bridge)

The current bridge calls core-WASM exports directly.

Required exports:

- `memory`
- `alloc(i32) -> i32`
- `dealloc(i32, i32)`
- `zeroclaw_tool_execute(i32, i32) -> i64`
- `zeroclaw_provider_chat(i32, i32) -> i64`

Conventions:

- Input is UTF-8 JSON written by host into guest memory.
- Return value packs output pointer/length into `i64`:
    - high 32 bits: pointer
    - low 32 bits: length
- Host reads UTF-8 output JSON/string and deallocates buffers.

Tool call payload shape:

```json
{
    "tool": "demo_tool",
    "args": { "key": "value" }
}
```

Provider call payload shape:

```json
{
    "provider": "demo-provider",
    "system_prompt": "optional",
    "message": "user prompt",
    "model": "model-name",
    "temperature": 0.7
}
```

Provider output may be either plain text or JSON:

```json
{
    "text": "response text",
    "error": null
}
```

If `error` is non-null, host treats the call as failed.

## Hot Reload

Manifest fingerprints are tracked internally and `hot_reload` is controlled by `[plugins].hot_reload`.

When enabled, the runtime refreshes its in-memory registry when plugin manifest fingerprints change.
When disabled, manifests are loaded only during initialization.

## Observer Bridge

Observer creation paths route through `ObserverBridge` to keep plugin runtime event flow compatible
with existing observer backends.

## Limitations

Current bridge is intentionally minimal:

- no full WIT component-model host bindings yet
- no per-plugin sandbox isolation beyond process/runtime defaults
- no signature verification or trust policy enforcement yet
- tool/provider manifests define registration; execution ABI is currently fixed to the core-WASM
  export contract above
