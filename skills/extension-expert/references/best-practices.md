# Extensions Best Practices

## Development
- **Structure**: Use `src/` for source and `dist/` for builds.
- **TypeScript**: Strongly recommended for type safety.
- **Bundling**: Use `esbuild` or `webpack` to bundle into `dist/`.
- **GEMINI.md**: Focus on high-level goals and tool usage.

## Security
- **Minimal Permissions**: Only request necessary tool access.
- **Exclude Tools**: Use `excludeTools` to block dangerous patterns.
- **Validate Inputs**: Always validate paths and arguments in MCP servers.
- **Sensitive Settings**: Use `sensitive: true` for API keys.

## Releasing
- **SemVer**: Follow Semantic Versioning rules.
- **Release Channels**: Use Git branches (e.g., `main` for stable).
- **Clean Artifacts**: Exclude `node_modules` and `src/` from releases.
