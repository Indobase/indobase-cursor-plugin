---
name: Create Indobase Project
description: Create a new Indobase project over the platform API, then switch into MCP-driven project setup.
---

Create a new Indobase project for me and connect this workspace to it.

Use this flow:

1. Verify I have an `INDOBASE_ACCESS_TOKEN`. If not, stop and ask me to create one first.
2. List my organizations using:
   `GET https://studio.indobase.in/api/platform/organizations`
   with `Authorization: Bearer <INDOBASE_ACCESS_TOKEN>`.
3. Ask me to choose the organization slug if there is more than one.
4. Ask for:
   - project name
   - region if needed
   - whether I want a random database password generated
5. Create the project with:
   `POST https://studio.indobase.in/api/platform/projects`
   using the bearer token.
6. After creation, construct:
   `INDOBASE_MCP_URL=https://studio.indobase.in/api/mcp?project_ref=<project-ref>&read_only=false&features=database,development,debugging`
7. Use MCP tools to confirm the project URL, publishable keys, and basic readiness.
8. If I want app scaffolding, continue by wiring the local codebase to the new project.
