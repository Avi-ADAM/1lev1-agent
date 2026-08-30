# 1lev1 for AI agents

Run your partnerships from the agent you already use.

[1lev1](https://1lev1.com) is a platform for **consent-based partnerships**.
People contribute work to a shared venture ("rikma"), the hours they log become
their documented share of it, and income is split by agreements everyone signs.
This repo publishes the **skill**: the standing instructions that teach your agent
what a rikma is, how consent works on the platform, and which of the ~20 MCP
tools to reach for. The MCP server gives an agent hands; this gives it judgement.

## Install (Claude Code)

```
/plugin marketplace add Avi-ADAM/1lev1-agent
```

```
/plugin install 1lev1@1lev1
```

Then connect your account:

```bash
npx 1lev1-mcp
```

Restart the client. That is it.

### Why the connection is a separate step

The plugin deliberately does **not** ship an MCP server entry. A bundled entry
would need your API key from an environment variable, and it would sit alongside
the one `npx 1lev1-mcp` writes — two servers, one of them broken, and an agent
seeing every tool twice. So there is exactly one connection path: the CLI, which
authenticates you in the browser and writes the key where your agent reads it.

If you install the skill without connecting, nothing breaks: the skill's first
instruction is to check, and to offer you the one-line fix.

## Other MCP clients

`npx 1lev1-mcp` also configures Cursor, Windsurf, Cline, Roo Code, Continue,
Antigravity, VS Code and Claude Desktop, and installs the skill where the client
reads it. To wire it by hand instead:

```json
{
  "mcpServers": {
    "1lev1": {
      "type": "http",
      "url": "https://api.1lev1.com/api/mcp",
      "headers": { "Authorization": "Bearer 1lev1_..." }
    }
  }
}
```

Get the key with `npx 1lev1-mcp`, or from Settings -> API keys on the site.

## What you can then say

- "What am I supposed to be working on today?"
- "Start the timer on the auth-refactor mission."
- "I worked 3 hours on the landing page yesterday - log it."
- "Turn this repo into a partnership with the three of us."
- "Draft missions for the open issues in this milestone."
- "What is waiting for my approval?"

## What it will not do

The plugin never votes, signs a profit-split, or accepts an offer on your behalf.
Anything that affects another person comes back as a prefilled link on the site
for a human to approve. That is the platform's model, not a limitation of the
plugin.

## Without an account

The server answers `getPlatformInfo` and `howToConnect` unauthenticated, so you
can ask your agent what 1lev1 is before signing up for anything.

## License

MIT
