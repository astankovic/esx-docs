---
title: "Routing"
section: "3"
slug: "routing"
sortOrder: 5
parentSection: null
sourceFiles:
  - "src/router/*"
---
This section covers **Routing**, the foundational system for mapping incoming HTTP requests to specific handlers based on methods like GET or POST and flexible path patterns. It's designed for developers building web applications and APIs, allowing precise control over request handling. Routing builds directly on [Getting Started](getting-started) for application setup and works alongside [Middleware](middleware) for preprocessing requests before they reach handlers. Once matched, routes produce responses covered in [Rendering Responses](rendering-responses); for static assets under routes, see [Static Files and Assets](static-files-and-assets).

## Overview
Routing enables defining endpoints that respond to specific HTTP methods and URL paths, including static matches, dynamic parameters (e.g., user IDs), wildcards for catch-all paths, and grouped prefixes for organizing APIs. Users specify patterns like exact paths, named captures, or regex-constrained segments, and handlers receive captured data for processing. Multiple matching routes execute in registration order, with priorities for exact over dynamic matches.

## Basic and Parametric Routes
Basic routes match exact paths for standard HTTP methods, while parametric routes capture variable segments from the URL into a key-value object accessible within the handler.

### Defining and Matching Routes
- Use static paths for fixed endpoints, such as a root or resource list.
- Parametric paths use colon-prefixed names (e.g., `:id`) to capture single segments.
- Wildcards (`*`) match remaining path segments greedily.
- Regex patterns constrain captures (e.g., `{[0-9]+}` for digits only).

When a request arrives:
1. The system checks the HTTP method and path against registered routes.
2. Matching routes (potentially multiple) are identified, with params populated (e.g., `/users/123` captures `{id: "123"}`).
3. Handlers for matches execute sequentially; exact static routes take precedence over params or wildcards.

| Pattern Type | Example Path | Captured Data | Description |
|--------------|--------------|---------------|-------------|
| **Static** | `/users` | None | Matches exact path only. |
| **Parametric** | `/users/:id` | `{ id: *segment-value* }` | Captures one path segment into named key. |
| **Wildcard** | `/files/*` | None (rest of path available via utilities) | Matches and consumes all remaining segments. |
| **Regex Parametric** | `/posts/:year{[0-9]{4}}` | `{ year: *matching-value* }` | Captures segment if it matches regex; rejects otherwise. |
| **Multi-segment Regex** | `/files/:path{.*}` | `{ path: *full-remaining-path* }` | Captures multiple segments with greedy regex. |

> [!NOTE]  
> Reserved words like `constructor` or `__proto__` work in params and wildcards without issues.

| Supported HTTP Methods | Description |
|------------------------|-------------|
| **GET** | Retrieve data (default for links). |
| **POST** | Submit data (e.g., forms). |
| **PUT** | Update/replace resources. |
| **PATCH** | Partial updates. |
| **DELETE** | Remove resources. |
| **OPTIONS** | Preflight checks (CORS). |
| **HEAD** | Metadata only (no body). |
| **TRACE**/**CONNECT** | Protocol-specific; rarely used. |

### Accessing Route Data in Handlers
Within a handler:
- Captured params appear as an object with keys like `id`, `year`.
- Route path (pattern as registered, e.g., `/users/:id`) via **route path**.
- Base path (prefix up to this route) via **base route path** or **base path** (resolved with captured values).

Example: For `/api/v1/users/123`, **route path** returns `/users/:id`; **base path** returns `/api/v1`.

## Route Groups and Nesting
Group related routes under a shared prefix using sub-applications, simplifying API organization (e.g., `/api/v1/*`).

### Setting Up Groups
1. Define a sub-application with its own routes.
2. Mount it at a base path (static or parametric).
3. Requests to the prefixed path inherit the group and execute sub-routes.

- Groups support parametric bases (e.g., `/api/:version/*` captures `version`).
- Nested groups chain prefixes (e.g., `/admin/:user/reports/*`).
- Matches include both group and child routes.

```mermaid
graph LR
    A[Request: GET /api/users/123] --> B{Matches Base /api?}
    B -->|Yes| C[Sub-App Routes: /users/:id]
    C --> D[Capture: {id: '123'}<br/>Handler Executes]
    E[Request: GET /admin/reports] --> F{Matches /admin/*?}
    F -->|Yes| G[Sub-App: /reports<br/>Inherits /admin Base]
    subgraph "Static Route"
        A1[GET /users] --> B1[Exact Match Handler]
    end
    subgraph "Parametric Route"
        C1[GET /users/:id] --> D1[Capture Param]
    end
    subgraph "Group/Nesting"
        E1[Mount /api at Sub-App] --> F1[Prefix All Sub-Routes]
    end
```

| Group Setting | Default | Options | What It Controls |
|---------------|---------|---------|------------------|
| **Base Path** | `/` | Static (e.g., `/api`), Parametric (e.g., `/:version`) | Prefix applied to all routes in the group. |
| **Inheritance** | Full | Captures from base flow to children | Params and path info available in nested handlers. |

## Utilities for Route Inspection
- **Matched routes**: Lists all routes that matched the request, including method, path, and order (useful for logging which handler responded).
- Index options: Use positive for earlier matches, negative (e.g., `-1`) for last.

## Troubleshooting
Common issues arise from unmatched paths or conflicting patterns.

| Message | Severity | Meaning |
|---------|----------|---------|
| No matching route found for method/path | Warning | Request path or method has no registered handler; check pattern typos or missing methods. Add wildcard fallback if needed. |
| Multiple matches, unexpected params | Info | Overlapping routes (e.g., `/posts/:id` and `/posts/123`) execute both; review order or specificity. |
| Regex param rejected | Error | Captured segment fails pattern (e.g., non-digits in `{[0-9]+}`); adjust regex or input validation. |

> [!WARNING]  
> Wildcards (`*`) are greedy and match across segments; place specific routes before catch-alls.

## Summary
- Define **static**, **parametric** (`:name`), **wildcard** (`*`), and **regex** routes for HTTP methods like **GET**/**POST**.
- Access captured params, **route path**, and **base path** directly in handlers.
- Use **route groups** for prefixed sub-applications to organize APIs.
- Matches prioritize exact > parametric; inspect via **matched routes** for debugging.

For setup, see [Getting Started](getting-started). Extend with [Middleware](middleware) or [WebSockets](websockets). Handle outputs in [Rendering Responses](rendering-responses).