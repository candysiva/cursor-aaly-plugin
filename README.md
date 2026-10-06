# Aaly

Describe the app you want. You get a real product: your data, a live API, sign-up, and an app people can open, use, and share, built with your coding agent.

## What you can build

A helpdesk. A booking system. Billing. Or the product you have in mind.

Start with one workflow, or design a complex system from the first conversation. Your agent keeps building on the same product as you ask for more.

## Connect

Aaly is a remote MCP server.

- **URL:** `https://mcp.aaly.io`
- **Transport:** Streamable HTTP
- **Sign-in:** OAuth 2.1 in your browser. No API key for everyday use.

Approve the consent screen when it opens. Create an account there if you need one, at [https://app.aaly.io](https://app.aaly.io).

### VS Code and GitHub Copilot

Create `.vscode/mcp.json` in your project:

```json
{
  "servers": {
    "aaly": {
      "type": "http",
      "url": "https://mcp.aaly.io"
    }
  }
}
```

Start the `aaly` server from Copilot chat and approve the sign-in screen.

### Cursor

Install **Aaly** from the Cursor Marketplace when it is listed: open **Customize**, search for Aaly, and select **Install**.

Or add the server yourself. Use `~/.cursor/mcp.json` for every project, or `.cursor/mcp.json` for this project:

```json
{
  "mcpServers": {
    "aaly": {
      "url": "https://mcp.aaly.io"
    }
  }
}
```

Open **Cursor Settings → MCP**, find `aaly`, and choose **Login / Connect**.

One-click install:

[cursor://anysphere.cursor-deeplink/mcp/install?name=aaly&config=eyJ1cmwiOiJodHRwczovL21jcC5hYWx5LmlvIn0=](cursor://anysphere.cursor-deeplink/mcp/install?name=aaly&config=eyJ1cmwiOiJodHRwczovL21jcC5hYWx5LmlvIn0=)

### Claude

Aaly is in the Claude connector directory: [https://claude.ai/directory/aaly](https://claude.ai/directory/aaly).

You can also add a custom connector with the URL `https://mcp.aaly.io`, then approve the sign-in screen.

### Other MCP clients

Point any client that supports a remote HTTP MCP server at `https://mcp.aaly.io` and complete the browser sign-in.

### CI and headless use

A Bearer API key from [https://app.aaly.io](https://app.aaly.io) is available only for CI and headless use, where a browser cannot open. Keep that key out of the repository.

## How to use

After you are connected, tell your agent what you want to build. Paste this:

```
Ask me what I want to build. Use Aaly so I end up with a real product I can open, sign into, and share. Show me the live link. Then ask what to add next.
```

Your agent will ask for the idea first. If you are stuck, it can start from a helpdesk, booking, or billing product and grow it with you.

## What Aaly gives your agent

Your agent creates a project and the data model for your product, and Aaly serves live API endpoints for that data. It can add custom endpoints and server-side functions, deploy that logic, and read request and function logs when something needs attention. It generates an OpenAPI spec for the project; the server URL in that spec is the live API your product uses. People sign up and use the app through that API.

## Cursor plugin

This repository is also the Aaly plugin for Cursor. Installing it adds:

- The Aaly MCP server at `https://mcp.aaly.io`
- The `build-fullstack-app` skill, which asks what you want, builds the product with Aaly, shows the live link and how to sign up, says plainly what is not available yet, and asks what to add next

To try the plugin from this repo before a marketplace install, copy it to:

```
~/.cursor/plugins/local/aaly
```

The folder needs `.cursor-plugin/plugin.json`. Restart Cursor, or run **Developer: Reload Window**, then open **Customize** and confirm the Aaly skill and the `aaly` server are listed. Local plugin imports must be allowed. If a marketplace plugin named `aaly` is already installed, that install takes precedence.

## Links

- [https://aaly.io](https://aaly.io)
- [Connect an AI agent](https://aaly.io/docs/connect)
- [Agent connection instructions](https://aaly.io/connect.md)
- [Limits](https://aaly.io/docs/limits)
- [Privacy](https://aaly.io/privacy)
- [App](https://app.aaly.io)
- MCP Registry name: `io.aaly/aaly`

## License

MIT. Copyright Aaly / Sivakumar Ganesan.
