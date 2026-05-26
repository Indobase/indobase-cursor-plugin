---
name: indobase-project-builder
description: Use when the user wants to connect Cursor to Indobase, create an Indobase project, inspect a project through MCP, or bootstrap an app against an Indobase project.
---

# Indobase project builder

Use Indobase in two layers:

1. **Platform HTTP API** for account, organization, and project lifecycle work.
2. **Indobase MCP** for project-scoped database, development, and debugging workflows.

## Defaults

- Prefer a **project-scoped MCP URL**.
- Prefer **read-only MCP** until the user explicitly asks for writes.
- Use an **Indobase access token** in the `Authorization: Bearer ...` header.

## Required env

- `INDOBASE_ACCESS_TOKEN`
- `INDOBASE_MCP_URL`

Optional if you need to call platform REST endpoints directly:

- `INDOBASE_BASE_URL` (default `https://studio.indobase.in`)

## Recommended MCP URL

For an existing project:

`https://studio.indobase.in/api/mcp?project_ref=<project-ref>&read_only=true&features=database,development,debugging`

Switch `read_only=true` to `false` only when the user wants migrations or other write operations.

## HTTP API workflow

When the user wants to create or select projects, use the platform API with the access token:

- `GET /api/platform/organizations`
- `GET /api/platform/projects`
- `POST /api/platform/projects`
- `GET /api/platform/projects/<ref>/api-keys`

Base URL:

`$INDOBASE_BASE_URL/api/platform/...`

## Create-project checklist

1. Confirm the target organization slug.
2. Gather the new project name.
3. Generate or ask for a database password.
4. Create the project through `POST /api/platform/projects`.
5. Build the project-scoped `INDOBASE_MCP_URL`.
6. Use MCP to inspect project URL, publishable keys, logs, and schema.
7. Only then scaffold or modify the local app.

## Bootstrap checklist

After MCP is connected:

1. Read project URL and publishable keys with MCP tools.
2. Inspect tables or current schema before generating code.
3. Create or update local env files only after confirming the app stack.
4. Use MCP write tools only with explicit user approval.
