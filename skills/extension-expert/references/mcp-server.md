# MCP Servers (Model Context Protocol)

MCP servers bridge Gemini CLI to external tools, APIs, and data.

## Capabilities
- **Tools**: List and execute structured tools.
- **Resources**: Expose data (files, APIs) via `@server://` URIs.
- **Prompts**: Predefined prompts usable as slash commands.

## Transport Types
1. **Stdio**: Local subprocess (most common for extensions).
2. **SSE**: Server-Sent Events (remote).
3. **HTTP**: Streamable HTTP.

## Manifest Configuration
In `gemini-extension.json`:
```json
"mcpServers": {
  "my-server": {
    "command": "node",
    "args": ["dist/server.js"],
    "env": { "DEBUG": "mcp:*" },
    "cwd": "${extensionPath}"
  }
}
```

## Security
- **Trust**: Use `trust` settings cautiously.
- **Environment**: Sensitive env vars are redacted by default.
- **Least Privilege**: Only include necessary tools via `includeTools`/`excludeTools`.
