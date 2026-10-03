---
name: build-fullstack-app
description: Build a full-stack app with Aaly. Ask for the app idea first. Aaly builds the backend (data and a live API); the coding agent builds a simple frontend. Use when the user wants to build, try, or start an app with Aaly, or is stuck and needs a starting idea.
---

# Build a full-stack app

This is the locked Aaly Try flow. Follow it in this order. Do not skip the question, and do not create a schema before the user answers.

The outcome is a full-stack app, not just a schema. Aaly builds the backend (data and a live API). You build a simple frontend that uses that API.

## 1. Ask for the idea first

Ask what app they want. Wait for an answer. Do not assume a todo list, and do not start building.

If they are stuck, suggest these and wait for them to pick one:

- helpdesk
- booking
- billing

## 2. Say limits plainly

Before creating anything, read the `aaly://platform/capabilities` resource and [Limits](https://aaly.io/docs/limits). If the idea depends on something Aaly does not do yet, say so in plain language before you build. Do not quietly work around a missing capability.

Say these gaps when they apply:

- No realtime. There are no WebSockets, push, or live subscriptions.
- No scheduled or cron execution. Server-side functions run only on a request.
- No role-based or field-level permissions. Access control is per tenant.
- No separate dev and production environments. Every project is live.
- No fuzzy search, MFA, password reset, or cursor pagination.

## 3. Aaly builds the backend

Aaly is the backend. Use the Aaly MCP tools to define the data and get a live API. Do not write backend code into the repository.

1. Call `whoami`. If it fails, the user still needs to approve the OAuth consent screen. They can sign up at https://app.aaly.io if they do not have an account.
2. Confirm the data model with them before `create_entity` or `create_field`: entities, fields, relationships, and whether the app is single-tenant or multi-tenant. Some of those choices are permanent.
3. Create the schema, then call `generate_openapi_spec`. The API link is `servers[0].url` in that spec. Do not invent a base URL.

## 4. Show the API link, signup, and a small frontend

When the backend is ready, give the user all three:

1. The API link (`servers[0].url` from the OpenAPI spec).
2. How to sign up: https://app.aaly.io (Google sign-in).
3. A small working frontend that you build against that API, including sign-up, sign-in, and the main screens.

End-user auth and data go through the REST API, not through MCP.
