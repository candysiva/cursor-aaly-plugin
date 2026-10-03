# Aaly for Cursor

Build a full-stack app from Cursor. Aaly is the backend API. Your agent builds the frontend.

You describe the app. Aaly defines the data and serves a live, multi-tenant REST API from that definition. No backend code is generated into your repository. The coding agent builds a small frontend against that API.

## Install from the Cursor Marketplace

1. Open **Customize** in the Cursor sidebar.
2. Search for **Aaly**.
3. Select **Install**.
4. Approve the OAuth consent screen in your browser. Sign up at [https://app.aaly.io](https://app.aaly.io) if you do not have an account yet.

No API key is pasted into the plugin. After it is connected, ask Cursor to build an app. The **Build a full-stack app** skill asks for your idea first (helpdesk, booking, or billing if you are stuck), has Aaly create the data and the live API, then builds a small frontend and shows you the API link.

## Fallback: add the MCP server directly

If the marketplace listing is not available yet, point Cursor at the Aaly server. This URL is the whole configuration:

```
https://mcp.aaly.io
```

Add it for every project in `~/.cursor/mcp.json`, or for this project only in `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "aaly": {
      "url": "https://mcp.aaly.io"
    }
  }
}
```

Then open **Cursor Settings → MCP**, find `aaly`, and click **Login / Connect**.

One-click install:

[cursor://anysphere.cursor-deeplink/mcp/install?name=aaly&config=eyJ1cmwiOiJodHRwczovL21jcC5hYWx5LmlvIn0=](cursor://anysphere.cursor-deeplink/mcp/install?name=aaly&config=eyJ1cmwiOiJodHRwczovL21jcC5hYWx5LmlvIn0=)

`config` is the base64 encoding of `{"url":"https://mcp.aaly.io"}`.

## OAuth

The server uses OAuth 2.1 with PKCE and dynamic client registration. Cursor requests `https://mcp.aaly.io`, follows the discovery metadata, and opens a consent screen in your browser. You approve it. The token is scoped to that connection and can be revoked from the Aaly dashboard. No key is shown or pasted.

How the flow works: [Connect an AI agent](https://aaly.io/docs/connect).

## Test the plugin locally

Copy this repository to:

```
~/.cursor/plugins/local/aaly
```

The folder must contain `.cursor-plugin/plugin.json`. Restart Cursor, or run **Developer: Reload Window**. Open **Customize** and confirm the Aaly skill and the `aaly` MCP server are listed.

Local plugin imports have to be allowed. On Teams and Enterprise, an admin controls that under **Dashboard → Settings → Security & Identity → Marketplace and Plugins**. If a marketplace plugin named `aaly` is already installed, that install takes precedence over this local copy.

## Links

- Sign up and dashboard: [https://app.aaly.io](https://app.aaly.io)
- Connect an agent: [https://aaly.io/docs/connect](https://aaly.io/docs/connect)
- Privacy: [https://aaly.io/privacy](https://aaly.io/privacy)
- Aaly: [https://aaly.io](https://aaly.io)
- MCP server: [https://mcp.aaly.io](https://mcp.aaly.io)

## License

MIT. Copyright Aaly / Sivakumar Ganesan.
