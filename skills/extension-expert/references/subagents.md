# Sub-agents (Experimental)

Sub-agents are specialized agents that handle complex tasks without cluttering the main context.

## Core Concepts
- **Specialists**: Each agent has its own persona, system prompt, and tools.
- **Tokens**: Separate context loops save tokens in the main session.
- **Discovery**: Main agent "hires" sub-agents via tools of the same name.

## Configuration
Enable in `settings.json`:
```json
"experimental": { "enableAgents": true }
```

## Creating Custom Sub-agents
Add Markdown files with YAML frontmatter to:
- Project: `.gemini/agents/*.md`
- User: `~/.gemini/agents/*.md`

### Frontmatter Example
```yaml
name: security-reviewer
description: Expert in identifying vulnerabilities.
tools: ["run_shell_command", "read_file"]
model: gemini-2.0-flash-thinking-exp
```

## Security ("YOLO Mode")
Sub-agents may execute tools without individual confirmation. Use caution with powerful tools.
