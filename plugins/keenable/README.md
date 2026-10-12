# Keenable plugin for Claude

Search the web and read pages as clean markdown from Claude with
[Keenable](https://keenable.ai), a web search engine built for AI agents.
**Keyless:** no signup and no API key.

The plugin connects Claude to Keenable's hosted MCP server and adds two skills:
one for everyday web lookups, one for multi-source research with citations.

## Install

**Claude Code**

```
/plugin marketplace add keenableai/keenable-claude-plugin
/plugin install keenable@keenable
```

Run `/mcp` to confirm the `keenable` server is connected with both tools, then
ask something that needs the live web.

**Claude (web, Desktop, Cowork)**

Add the plugin from the directory in Claude once it is listed. Until then, the
same server is available as the **Keenable Web Search** connector in
**Customize → Connectors**.

## Tools

| Tool | What it does |
|---|---|
| `search_web_pages` | Ranked web results with an excerpt of each page, narrowed by site or publication date when needed. |
| `fetch_page_content` | Any URL as clean markdown, or only the part an extraction prompt asks for. |

## Skills

| Skill | What it does |
|---|---|
| `keenable-web` | Everyday web lookups: when to search, when to read a page, how to cite. |
| `keenable-deep-research` | Breaks a broad question into sub-questions, reads the strongest sources, cross-checks, and writes a cited answer. |

## Example prompts

```text
Find the release notes for every version of zod between the one in package.json
and the latest, list the breaking changes, and update our schemas to match.
```

```text
Look for reports of this error on github.com from the last 30 days and tell me
whether there is a known fix.
```

```text
Research the leading agent observability platforms and compare them in a table,
with a source link for every claim.
```

## Higher rate limits

The plugin sends no credentials, so it runs on Keenable's shared public tier
([rate limits](https://docs.keenable.ai/rate-limits)). To use your own Keenable
account instead:

- **Claude Code:** add the same server yourself with an API key from the
  [console](https://app.keenable.ai/console). Claude Code then skips the
  plugin's keyless copy of it, so the tools are not listed twice, and the
  skills keep working with your server:

  ```bash
  claude mcp add --transport http --scope user keenable https://api.keenable.ai/mcp \
    --header "X-API-Key: keen_<your_key>"
  ```

- **Claude (web, Desktop, Cowork):** add a custom connector with the URL
  `https://api.keenable.ai/mcp-oauth` and sign in to Keenable. See the
  [Claude guide](https://docs.keenable.ai/integrations/claude#use-your-own-account).

## Data and security

The plugin talks only to `https://api.keenable.ai/mcp` over HTTPS. Search
queries and requested URLs are sent to Keenable, along with an
`X-Keenable-Title: claude-plugin` header that identifies the plugin's traffic.
It sends no credentials, runs no local code or shell commands, and reads no
local files. See the [privacy policy](https://keenable.ai/privacy).

## Resources

- [Keenable](https://keenable.ai)
- [Documentation](https://docs.keenable.ai)
- [Support](https://keenable.ai/contact)

## License

MIT
