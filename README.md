# 1lev1 for AI agents

Run your partnerships from the agent you already use.

[1lev1](https://1lev1.com) is a platform for **consent-based partnerships**.
People contribute work to a shared venture ("rikma"), the hours they log become
their documented share of it, and income is split by agreements everyone signs.
This repo publishes the 1lev1 plugin: an MCP connection plus a skill that teaches
your agent how the platform actually works.

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

## Other MCP clients

Add the server to your client config and the skill folder to wherever your client
reads skills from:

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
