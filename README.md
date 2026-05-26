# Indobase Cursor Plugin

Cursor plugin for connecting Cursor to **Indobase** with the hosted, OAuth-backed MCP server.

It gives users:

- a prewired **Indobase MCP server** entry that is ready to authenticate in Cursor
- a focused **Indobase skill** for sign-in, project selection, creation, and bootstrapping
- reusable **commands** for authenticating, connecting, creating, and building against Indobase projects

## What it does

This plugin is now **OAuth-first**:

1. It installs a hosted **Indobase MCP** connection.
2. Cursor can authenticate the MCP server through the normal MCP login flow.
3. After sign-in, the agent can list organizations, create projects, connect to existing projects, and use project tools from inside the editor.

## File tree

```text
indobase-cursor-plugin/
  .cursor-plugin/plugin.json
  .mcp.json
  README.md
  LICENSE
  CHANGELOG.md
  commands/
    authenticate-indobase.md
    build-with-indobase.md
    connect-indobase-project.md
    create-indobase-project.md
  skills/
    indobase-project-builder/SKILL.md
```

## Hosted setup

No token env vars are required for the default hosted experience.

The plugin ships with this MCP config:

```json
{
  "mcpServers": {
    "indobase": {
      "url": "https://mcp.indobase.in?features=account,database,development,debugging"
    }
  }
}
```

## Recommended setup

1. Install the plugin.
2. Restart Cursor if the MCP server does not appear immediately.
3. Open **Settings > Cursor Settings > Tools & MCP**.
4. Find the `indobase` server and authenticate when prompted.
5. After sign-in, use the plugin commands or ask naturally to list or create projects.

## Optional advanced override

If you want a narrower, project-scoped MCP URL after initial sign-in, use:

```text
https://mcp.indobase.in?project_ref=<project-ref>&read_only=true&features=database,development,debugging
```

This is useful when you want to reduce tool scope after choosing a project.

## Commands

- `Authenticate Indobase`
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

- The default MCP endpoint used by this plugin is `https://mcp.indobase.in`.
- The plugin is designed to authenticate through MCP/OAuth first, instead of requiring a manually created bearer token.
- Project creation and discovery should prefer MCP account tools when available.
- For safety, use non-production projects whenever possible.
