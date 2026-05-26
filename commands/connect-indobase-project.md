---
name: Connect Indobase Project
description: Connect this workspace to an existing Indobase project through the Indobase MCP server.
---

Help me connect this workspace to an existing Indobase project.

Workflow:

1. Check whether the hosted `indobase` MCP server is authenticated in Cursor.
2. If not authenticated, guide me through the MCP OAuth sign-in flow first.
3. Use MCP account tools to list my projects unless I already know the project ref.
4. Ask whether I want read-only or write access. Default to read-only.
5. Once the target project is known, switch to the recommended scoped MCP URL shape:
   `https://mcp.indobase.in?project_ref=<project-ref>&read_only=<true|false>&features=database,development,debugging`
6. After the MCP server is available, use Indobase MCP tools to:
   - inspect the project URL
   - fetch publishable keys
   - inspect tables or schema
   - check recent logs if relevant
7. Keep the session read-only unless I explicitly ask for mutations.
