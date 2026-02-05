# Extensions Creator 🛠️

A specialized Gemini CLI extension designed to scaffold, validate, and bootstrap new Gemini CLI extensions following official best practices and standards.

## Features

- **Expert Scaffolding**: Automates the creation of manifests, directory structures, and skills.
- **Knowledge Base**: Includes a built-in library of official documentation for Agent Skills, MCP servers, Hooks, and more.
- **Wizard Driven**: Use `/new-extension` to trigger an interactive development session with the `extension-expert` skill.
- **Best Practices**: Ensures all generated skills have mandatory YAML frontmatter and proper directory layouts.

## Commands

| Command | Description | Action |
| :--- | :--- | :--- |
| `/new-extension` | Extension Wizard | Activates the `extension-expert` skill to guide you through creating a new extension. |

## Knowledge Base
The extension bundles official documentation as static references within the `extension-expert` skill:
- Agent Skills
- MCP Server Configuration
- Hooks Reference
- Best Practices & Security
- Releasing & Distribution

## Installation

### From Source
1. Clone this repository.
2. Link the extension to your Gemini CLI:
   ```bash
   gemini extensions link .
   ```

## Structure

```
extensions-creator/
├── gemini-extension.json  # Manifest
├── GEMINI.md             # Persistent context
├── commands/             # /new-extension definition
└── skills/
    └── extension-expert/ # The "brain" of the creator
        ├── SKILL.md      # Expert instructions
        └── references/   # Bundled documentation
```

## License
MIT
