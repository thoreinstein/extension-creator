# Gemini CLI Hooks

Hooks allow you to intercept and customize CLI behavior at specific lifecycle events.

## Triggers
- `SessionStart`
- `BeforeAgent`
- `AfterModel`
- `BeforeToolSelection`
- `AfterTool`

## Key Requirements
- **Communication**: Use `stdin` (input) and `stdout` (output).
- **Format**: `stdout` MUST be a single, final JSON object.
- **Logging**: Use `stderr` for all debugging and logs.
- **Exit Codes**:
  - `0`: Success
  - `2`: System Block (blocks the agent's next action)
  - Other: Warning

## Configuration
Defined in `hooks/hooks.json` for extensions or `settings.json` for users.
```json
{
  "name": "my-hook",
  "trigger": "AfterModel",
  "command": "node my-hook.js"
}
```

## Security
Hooks execute arbitrary code with user privileges. Project-level hooks are fingerprinted and require user confirmation if they change.
