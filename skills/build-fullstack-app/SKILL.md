---
name: build-fullstack-app
description: Build a real product with Aaly. Ask what they want first. Aaly provides the data and the live API; you build an app people can open, sign into, and share, and that can grow into a complex system. Use when someone wants to build, try, or extend a product with Aaly, or is stuck and needs a starting idea.
---

# Build a full-stack app

Follow this flow in order. The result is a real product someone can open, sign into, and share. It can start as one workflow and grow into a complex system.

## 1. Ask for the idea first

Ask what they want to build. Wait for an answer before you create anything. Do not assume a todo list.

If they are stuck, suggest these and wait for them to pick one:

- helpdesk
- booking
- billing

## 2. Build it with Aaly

Aaly provides the data and the live API. You build the product people use.

1. Call `whoami`. If it fails, they still need to approve the browser sign-in. They can create an account at https://app.aaly.io.
2. Read `aaly://platform/capabilities` and https://aaly.io/docs/limits. If the idea depends on something Aaly does not do yet, say so in plain language before you build.
3. Confirm what the product stores, how those records relate, and whether each customer organization keeps its own data, before `create_entity` or `create_field`. Some of those choices are permanent.
4. Create the project and the data model. Call `generate_openapi_spec`. The live API link is `servers[0].url` in that spec. Do not invent a base URL.
5. Build the app against that API so people can sign up, sign in, and use the product. Accounts and records go through the REST API, not through MCP.

## 3. Show the live link and sign-up

When the product is ready, give them:

1. The live link: where to open the app, and the API URL from `servers[0].url`.
2. How to sign up: https://app.aaly.io

## 4. Be honest about what is not there yet

Say plainly what this product still cannot do on Aaly. Mention a gap when it applies:

- Realtime updates
- Scheduled or cron jobs
- Role-based permissions
- A separate place to try changes before they are live
- Fuzzy search, MFA, password reset, or deep cursor pagination

The full list is at https://aaly.io/docs/limits.

## 5. Ask what to add next

Ask what they want to add next, and keep building on the same product.
