# Extensions Reference

## gemini-extension.json Structure
```json
{
  "name": "my-extension",
  "version": "1.0.0",
  "description": "...",
  "mcpServers": {
    "my-server": { "command": "node my-server.js" }
  },
  "contextFileName": "GEMINI.md",
  "excludeTools": ["run_shell_command(rm -rf *)"]
}
```

- **name**: Lowercase, dash-separated. Must match directory name.
- **mcpServers**: Map of server names to configurations.
- **contextFileName**: Defaults to `GEMINI.md`.
- **excludeTools**: Array of tools or specific command patterns to block.

## Directory Conventions
- **Commands**: `commands/` directory (TOML files).
- **Hooks**: `hooks/hooks.json` file.
- **Skills**: `skills/<skill-name>/SKILL.md`.
- **Sub-agents**: `agents/` directory (Markdown files).

## Variables
- `${extensionPath}`: Absolute path to the extension.
- `${workspacePath}`: Path to current workspace.
- `${/}`: OS-specific path separator.
