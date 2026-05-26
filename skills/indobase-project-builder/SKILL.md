---
name: indobase-project-builder
description: Use when the user wants to connect Cursor to Indobase, create an Indobase project, inspect a project through MCP, or bootstrap an app against an Indobase project.
---

# Indobase project builder

Use Indobase through the hosted MCP server first.

1. **Hosted Indobase MCP** for authentication, account discovery, project selection, creation, database work, development, and debugging.
2. **Platform HTTP API** only as a fallback when MCP account tools are unavailable for the current client.

## Defaults

- Prefer the hosted OAuth-backed MCP connection.
- Start unscoped if the user may need to list or create projects.
- Narrow to a **project-scoped MCP URL** after project selection when appropriate.
- Prefer **read-only MCP** until the user explicitly asks for writes.

## Default hosted MCP URL

`https://mcp.indobase.in?features=account,database,development,debugging`

## Recommended project-scoped MCP URL

`https://mcp.indobase.in?project_ref=<project-ref>&read_only=true&features=database,development,debugging`

Switch `read_only=true` to `false` only when the user wants migrations or other write operations.

## OAuth workflow

1. Ensure the `indobase` MCP server is installed in Cursor.
2. If tools are unavailable due to auth, tell the user to authenticate the MCP server in **Tools & MCP**.
3. After authentication, prefer MCP account tools to list organizations, list projects, and create projects.
4. Once the target project is known, use project tools to inspect URLs, keys, schema, logs, and functions.

## Create-project checklist

1. Confirm the MCP server is authenticated.
2. List organizations or projects before guessing identifiers.
3. Ask the user to choose an organization if needed.
4. Create the project with MCP account tools when available.
5. Narrow to the target project context.
6. Inspect project URL, publishable keys, logs, and schema.
7. Only then scaffold or modify the local app.

## Bootstrap checklist

After MCP is connected:

1. Read project URL and publishable keys with MCP tools.
2. Inspect tables or current schema before generating code.
3. Create or update local env files only after confirming the app stack.
4. Use MCP write tools only with explicit user approval.
5. Fall back to the platform HTTP API only when MCP account tooling is not available in the current client.
