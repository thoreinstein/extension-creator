# Extension Releasing

## 1. Git Repository (Simplest)
- Users install via: `gemini extensions install <repo-url>`
- Support multiple channels via branches/tags (e.g., `--ref=stable`).

## 2. GitHub Releases (Efficient)
- Faster initial install (downloads archives).
- Gemini looks for the "latest" release unless `--ref` is specified.

## Platform Specific Archives
Naming convention: `{platform}.{arch}.{name}.{extension}`
- **Platforms**: `darwin`, `linux`, `win32`
- **Arch**: `x64`, `arm64`

## Archive Structure
Archives must have `gemini-extension.json` at the root and follow the standard extension layout.
