# Custom Commands in Gemini CLI

Custom commands in Gemini CLI allow users to save and reuse frequently used prompts as personal shortcuts, either globally or per project. This streamlines workflows and ensures consistency.

## File Locations and Precedence

Gemini CLI discovers commands from two locations:
- **User commands (global):** Located in `~/.gemini/commands/`. These are available across all projects.
- **Project commands (local):** Located in `<your-project-root>/.gemini/commands/`. These are specific to the current project and can be version-controlled.

Project commands take precedence over user commands if they share the same name.

## Naming and Namespacing

A command's name is determined by its file path relative to its commands directory. Subdirectories create namespaced commands, with path separators (`/` or ``) converted to a colon (`:`).
- Example: `~/.gemini/commands/test.toml` becomes `/test`.
- Example: `<project>/.gemini/commands/git/commit.toml` becomes `/git:commit`.

## TOML File Format (v1)

Command definition files must be in TOML format with a `.toml` extension.

### Required Fields
- `prompt` (String): The prompt sent to the Gemini model when the command is executed. Can be single or multi-line.

### Optional Fields
- `description` (String): A brief, one-line description displayed in the `/help` menu. If omitted, a generic description is generated from the filename.

## Handling Arguments

Custom commands support two methods for handling arguments, chosen automatically based on the `prompt` content.

### 1. Context-aware injection with `{{args}}`

If the prompt contains `{{args}}`, it's replaced with the text the user typed after the command name.

- **Raw injection (outside shell commands):** Arguments are injected exactly as typed.
  - Example: `prompt = "Please provide a code fix for the issue described here: {{args}}."`
- **Using arguments in shell commands (inside `!{...}` blocks):** Arguments are automatically shell-escaped before replacement, preventing command injection vulnerabilities.
  - Example: `prompt = "Please summarize the findings for the pattern {{args}}. Search Results: !{grep -r {{args}} .}"`

### 2. Default argument handling

If the prompt does not contain `{{args}}`, the CLI uses a default behavior:
- If arguments are provided (e.g., `/mycommand arg1`), the full command typed by the user is appended to the end of the prompt, separated by two newlines.
- If no arguments are provided, the prompt is sent as is.

## Executing Shell Commands with `!{...}`

Shell commands can be executed directly within the prompt using `!{...}` syntax, and their output is injected. This is useful for gathering context from the local environment (e.g., `git diff --staged`).
- The CLI prompts for confirmation before executing shell commands as a security measure.
- `{{args}}` inside `!{...}` blocks are shell-escaped.
- The parser handles complex shell commands with nested braces.
- If a command fails, error messages (stderr) and a status line are injected into the prompt.

## Injecting File Content with `@{...}`

The content of a file or a directory listing can be embedded directly into the prompt using `@{...}` syntax. This is useful for commands operating on specific files.
- `@{path/to/file.txt}` is replaced by the file's content.
- Supports multimodal files (images, PDFs, audio, video) which are encoded and injected. Other binary files are skipped.
- `@{path/to/dir}` traverses the directory and inserts each file's content, respecting `.gitignore` and `.geminiignore`.
- Paths are workspace-aware.
- File content injection (`@{...}`) is processed before shell commands (`!{...}`) and argument substitution (`{{args}}`).
