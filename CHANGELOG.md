# Changelog

## 0.1.1

- Switched the plugin to the hosted Indobase MCP endpoint for OAuth-first sign-in.
- Removed the default requirement for manual access-token headers.
- Updated commands and docs to guide users through MCP authentication and project selection inside Cursor.

## 0.1.0

- Initial Cursor plugin release for Indobase.
- Added remote MCP configuration using `INDOBASE_MCP_URL` and `INDOBASE_ACCESS_TOKEN`.
- Added commands for connecting an existing project, creating a project, and building with Indobase.
- Added `indobase-project-builder` skill for safe MCP-first workflows.
