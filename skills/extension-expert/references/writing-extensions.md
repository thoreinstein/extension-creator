# Getting started with Gemini CLI extensions

This guide walks you through creating your first Gemini CLI extension. You'll learn how to set up a new extension, add a custom tool via an MCP server, create a custom command, and provide context to the model with a GEMINI.md file.

## Feature Overview
| Feature | What it is | When to use it | Invoked by |
| :--- | :--- | :--- | :--- |
| **MCP server** | A standard way to expose new tools and data sources. | When you want the model to do new things. | Model |
| **Custom commands** | A shortcut (like `/my-cmd`) for prompts or shell commands. | For repetitive tasks or complex prompts. | User |
| **Context file (GEMINI.md)** | Persistent context loaded into every session. | Define personality or coding standards. | CLI |
| **Agent skills** | Specialized instructions and workflows activated as needed. | For complex, occasional tasks. | Model |

## Step-by-Step
1. **Create**: `gemini extensions new my-first-extension mcp-server`
2. **Link**: `gemini extensions link .` (Use this for local development).
3. **Command**: Add TOML files in `commands/`.
4. **Context**: Add `GEMINI.md` and set `contextFileName` in manifest.
5. **Skills**: Add `skills/security-audit/SKILL.md` (MUST have YAML frontmatter).
