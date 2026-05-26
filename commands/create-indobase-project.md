---
name: Create Indobase Project
description: Create a new Indobase project over the platform API, then switch into MCP-driven project setup.
---

Create a new Indobase project for me and connect this workspace to it.

Use this flow:

1. Verify that the hosted `indobase` MCP server is authenticated in Cursor. If not, complete MCP OAuth login first.
2. List my organizations using MCP account tools.
3. Ask me to choose the organization slug if there is more than one.
4. Ask for:
   - project name
   - region if needed
   - whether I want a random database password generated
5. Create the project with MCP account tools when available.
6. After creation, continue with the project through MCP and narrow to a project-scoped URL when appropriate:
   `https://mcp.indobase.in?project_ref=<project-ref>&read_only=false&features=database,development,debugging`
7. Use MCP tools to confirm the project URL, publishable keys, and basic readiness.
8. If the current client lacks MCP account tools, fall back to the Indobase platform API only as a backup path.
9. If I want app scaffolding, continue by wiring the local codebase to the new project.
