# AALY

Build and host full-stack apps with your coding agent, no AI credits. Your idea + your coding agent + AALY = a live app.

Connect Cursor, Claude or VS Code with Copilot to `https://mcp.aaly.io`. Your agent defines the backend instead of coding it (database, REST API, sign-in, files, notifications, Python Functions), writes the frontend, and publishes it to `https://<name>.aaly.cloud`. It follows a guided build: questions first, a plan you approve, every business rule tested with sample data, and a user guide at handover.

Start with a helpdesk, a booking system or a client portal, and keep evolving the same app without breaking what already works.

## Connect

AALY is a remote MCP server.

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

Use `~/.cursor/mcp.json` for every project, or `.cursor/mcp.json` for this project:

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

[Add AALY to Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=aaly&config=eyJ1cmwiOiJodHRwczovL21jcC5hYWx5LmlvIn0=)

### Claude

In Claude, search for AALY under Settings → Connectors, or add a custom connector with the URL `https://mcp.aaly.io`, then approve the sign-in screen.

### Other MCP clients

Point any client that supports a remote HTTP MCP server at `https://mcp.aaly.io` and complete the browser sign-in.

### CI and headless use

A Bearer API key from [https://app.aaly.io](https://app.aaly.io) is available only for CI and headless use, where a browser cannot open. Keep that key out of the repository.

## How to use

After you are connected, tell your agent what you want to build. Paste this:

```
Ask me what I want to build. Use AALY so I end up with a real product I can open, sign into, and share. Show me the live link. Then ask what to add next.
```

Your agent will ask for the idea first. If you are stuck, it can start from a helpdesk, booking, or billing product and grow it with you.

## What AALY gives your agent

Your agent creates a project and the data model for your product, and AALY serves live API endpoints for that data. It can add custom endpoints and server-side functions, deploy that logic, and read request and function logs when something needs attention. It generates an OpenAPI spec for the project; the server URL in that spec is the live API your product uses. People sign up and use the app through that API.

## Cursor plugin

This repository is also the AALY plugin for Cursor. Installing it adds:

- The AALY MCP server at `https://mcp.aaly.io`
- The `build-fullstack-app` skill, which asks what you want, builds the product with AALY, shows the live link and how to sign up, says plainly what is not available yet, and asks what to add next

To install the plugin from this repo, copy it to:

```
~/.cursor/plugins/local/aaly
```

The folder needs `.cursor-plugin/plugin.json`. Restart Cursor, or run **Developer: Reload Window**, then open **Customize** and confirm the AALY skill and the `aaly` server are listed. Local plugin imports must be allowed.

## Links

- [https://aaly.io](https://aaly.io)
- [Connect an AI agent](https://aaly.io/docs/connect)
- [Agent setup](https://aaly.io/connect.md)
- [Frontend hosting](https://aaly.io/docs/hosting)
- [Limits](https://aaly.io/docs/limits)
- [Privacy](https://aaly.io/privacy)
- [App](https://app.aaly.io)
- MCP Registry name: `io.aaly/aaly`

## License

MIT. Copyright AALY.
