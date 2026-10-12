# Keenable plugin for Claude

Keyless web search and clean page extraction for Claude through
[Keenable](https://keenable.ai)'s hosted MCP server, with skills for everyday
web lookups and cited multi-source research.

The plugin lives in [`plugins/keenable`](./plugins/keenable); its
[README](./plugins/keenable/README.md) covers the tools, skills, rate limits and
data handling.

## Install in Claude Code

```
/plugin marketplace add keenableai/keenable-claude-plugin
/plugin install keenable@keenable
```

## Repository layout

| Path | What it is |
|---|---|
| `plugins/keenable/` | The plugin: manifest, `.mcp.json`, skills, logo. |
| `.claude-plugin/marketplace.json` | Lets Claude Code install the plugin from this repo. |
| `.github/`, `.gitleaks.toml`, `scripts/` | Repository CI (secret scanning). Not part of the plugin. |

## License

MIT
