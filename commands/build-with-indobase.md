---
name: Build With Indobase
description: Use an Indobase project to scaffold or wire up the current app from inside Cursor.
---

Use Indobase to help build this project.

Process:

1. Confirm whether I already have an Indobase project ref. If not, offer to create one first.
2. Confirm that the Indobase MCP server is connected.
3. Inspect the current project through MCP before making changes:
   - project URL
   - publishable keys
   - current schema/tables
   - recent logs if debugging is needed
4. Ask what stack I want to build in this workspace.
5. Generate only the minimum code needed to connect the local app to Indobase.
6. If database changes are required, explain the migration plan first and only write through MCP after I approve it.
7. Prefer safe, reviewable steps over one-shot large changes.
