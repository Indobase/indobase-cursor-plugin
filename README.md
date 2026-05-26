# Indobase Cursor Plugin

Cursor plugin for connecting Cursor to **Indobase**.

It gives users:

- a prewired **Indobase MCP server** entry
- a focused **Indobase skill** for project creation and bootstrapping
- reusable **commands** for connecting, creating, and building against Indobase projects

## What it does

This plugin uses two integration paths:

1. **Indobase MCP** for project-scoped database, development, and debugging work.
2. **Indobase platform HTTP API** for listing organizations, creating projects, and fetching project-level details.

## File tree

```text
indobase-cursor-plugin/
  .cursor-plugin/plugin.json
  .mcp.json
  README.md
  LICENSE
  CHANGELOG.md
  commands/
    build-with-indobase.md
    connect-indobase-project.md
    create-indobase-project.md
  skills/
    indobase-project-builder/SKILL.md
```

## Required env vars

Set these somewhere Cursor can read them:

```bash
export INDOBASE_ACCESS_TOKEN="..."
export INDOBASE_MCP_URL="https://studio.indobase.in/api/mcp?project_ref=<project-ref>&read_only=true&features=database,development,debugging"
```

## Recommended setup

1. Create an Indobase access token in your account settings.
2. Start with a **project-scoped** MCP URL.
3. Keep `read_only=true` until you actually want migrations or writes.
4. Restart Cursor if the plugin or MCP server does not appear immediately.

## Example MCP config

```json
{
  "mcpServers": {
    "indobase": {
      "type": "http",
      "url": "${INDOBASE_MCP_URL}",
      "headers": {
        "Authorization": "Bearer ${INDOBASE_ACCESS_TOKEN}"
      }
    }
  }
}
```

## Commands

- `Connect Indobase Project`
- `Create Indobase Project`
- `Build With Indobase`

## Suggested prompts

- "Connect this repo to my Indobase project"
- "Create a new Indobase project for this app"
- "Use Indobase MCP to inspect my schema and wire up auth"

## Publish checklist

1. Push this folder to a **public Git repository**.
2. Submit the repository at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish).
3. Wait for Cursor review.

## Notes

- The MCP endpoint used by this plugin is `https://studio.indobase.in/api/mcp`.
- Project creation currently goes through the platform HTTP API, then hands off to MCP for project-scoped work.
- For safety, use non-production projects whenever possible.
