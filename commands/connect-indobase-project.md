---
name: Connect Indobase Project
description: Connect this workspace to an existing Indobase project through the Indobase MCP server.
---

Help me connect this workspace to an existing Indobase project.

Workflow:

1. Ask for my Indobase project ref if it is not already known.
2. Ask whether I want read-only or write access. Default to read-only.
3. Tell me the exact env vars I need to set for Cursor:
   - `INDOBASE_ACCESS_TOKEN`
   - `INDOBASE_MCP_URL`
4. Build the recommended MCP URL in this format:
   `https://studio.indobase.in/api/mcp?project_ref=<project-ref>&read_only=<true|false>&features=database,development,debugging`
5. After the MCP server is available, use Indobase MCP tools to:
   - inspect the project URL
   - fetch publishable keys
   - inspect tables or schema
   - check recent logs if relevant
6. Keep the session read-only unless I explicitly ask for mutations.
