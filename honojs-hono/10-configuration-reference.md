---
title: "Configuration Reference"
section: "10"
slug: "configuration-reference"
sortOrder: 22
parentSection: null
sourceFiles:
  - "src/preset/*"
  - "src/router/*"
  - "package.json"
---
This section covers the Configuration Reference, providing options to customize your Hono application for performance, bundle size, and deployment needs. It's designed for users optimizing applications after initial setup, such as selecting lightweight presets or tuning routers for specific workloads. This builds on core setup in [Getting Started](getting-started) and integrates with deployment choices in [Runtime Adapters and Deployment](runtime-adapters-and-deployment). For route handling affected by these settings, see [Routing](routing).

## Overview
Configuration lets you tailor the framework's behavior through presets for quick starts with minimal overhead, custom router algorithms for matching efficiency, environment variables for runtime tweaks, and adapter-specific options for deployments like edge workers or servers. These settings control bundle size, matching speed, strictness, and environment awareness without altering your routes or middleware.

## Presets
Presets offer pre-optimized variants of the framework, balancing features and size. Choose a preset based on your needs: **tiny** for the absolute smallest footprint, **quick** for a bit more convenience with still-low overhead, or the full version for all capabilities.

| Preset | Bundle Size | Included Features | Best For |
|-------|-------------|-------------------|----------|
| **tiny** | *~3 KB* | Basic routing only | Edge environments, strict size limits (e.g., Cloudflare Workers) |
| **quick** | *~6 KB* | Basic routing + essential helpers (e.g., cookie parsing) | Rapid prototyping with minimal extras |
| **full** (default) | *~12 KB* | All routing, middleware support, JSX, utilities | Feature-rich apps, server runtimes |

> [!NOTE]  
> Switch presets by selecting the corresponding variant during app initialization. Bundle sizes are approximate minified+gzip.

## Custom Routers
Custom routers adjust how incoming requests are matched to your defined paths, optimizing for route count, pattern complexity, or environment constraints. Configure the **Router Type** to balance speed and memory.

| Router Type | Matching Speed | Memory Usage | Use Cases |
|-------------|----------------|--------------|-----------|
| **RegExp** | *High* (parallel checks) | *Low* | Complex parametric routes, many wildcards (*, :id) |
| **Trie** | *Very High* (prefix tree) | *Medium* | REST APIs, hierarchical routes with common prefixes |
| **Linear** | *Medium* (sequential scan) | *Very Low* | Few routes (<50), memory-constrained environments |

Set the **Router Type** in app options. Defaults to **Trie** for most cases. Test performance with your route set for best results.

> [!WARNING]  
> Changing router types mid-development may affect route matching order; re-test all paths.

## Environment Variables
Use environment variables to control global behaviors like development mode, strict parsing, or logging verbosity without code changes. Set them in your shell, .env file, or deployment platform.

| Variable | Default | Accepted Values | What It Controls |
|----------|---------|-----------------|------------------|
| **HONO_MODE** | *development* | *development*, *production* | Enables/disables dev logging, loose param parsing; *production* enforces strict mode |
| **HONO_PORT** | *3000* | Any valid port (e.g., *8080*) | Listening port for server runtimes (ignored in edge) |
| **HONO_LOG_LEVEL** | *info* | *debug*, *info*, *warn*, *error* | Console output detail; *debug* shows route matches |
| **HONO_STRICT** | *false* | *true*, *false* | Enforces trailing slashes and param validation |

> [!NOTE]  
> Prefix with your runtime (e.g., **DENO_HONO_MODE**) for conflicts.

## Runtime-Specific Settings
These extend presets and routers for deployment platforms. Configure via app options or env vars tied to the adapter.

| Runtime | Key Settings | Default | Notes |
|---------|--------------|---------|-------|
| **Cloudflare Workers/Pages** | **globalPrefix**, **wasmBindgen** | None | Prefix all routes; enable WASM for crypto |
| **Deno** | **cacheModules**, **permissions** | *true* | Auto-cache deps; set --allow-net flags |
| **Bun/Node** | **hotReload**, **watchPaths** | *false* | Enable dev server reload; specify directories |
| **Fastly/Lambda** | **maxBodySize**, **timeoutMs** | Platform default | Limit request size; set response deadlines |

For full adapter details, see [Runtime Adapters and Deployment](runtime-adapters-and-deployment).

## Summary
- Use **Presets** (**tiny**, **quick**) to minimize bundle size while retaining core routing.
- Select **Custom Routers** (**RegExp**, **Trie**, **Linear**) for optimal path matching based on your route complexity.
- Set **Environment Variables** like **HONO_MODE** for mode-specific behaviors across deploys.
- Apply **Runtime-Specific Settings** to fine-tune for platforms like Cloudflare or Deno, complementing [Runtime Adapters and Deployment](runtime-adapters-and-deployment).
- Related: [Getting Started](getting-started) for initial config, [Routing](routing) for path impacts.