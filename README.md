# @boomi/embedkit-cdn

CDN distribution package for [Boomi EmbedKit](https://github.com/OfficialBoomi/embedkit) — the pre-built JavaScript bundle that lets you embed Boomi AI Agents into any website with a few lines of HTML. No React, no npm, no build pipeline required.

---

## What Is EmbedKit?

[Boomi EmbedKit](https://github.com/OfficialBoomi/embedkit) is a React component library that surfaces Boomi AI Agents inside any web application. It handles authentication, session management, real-time streaming, and rendering of the full agent chat UI — all inside a Shadow DOM so it never conflicts with your existing styles.

EmbedKit comes in two forms:

| Package | Use case |
|---------|----------|
| [`@boomi/embedkit`](https://www.npmjs.com/package/@boomi/embedkit) | React apps — import components and hooks directly |
| [`@boomi/embedkit-cdn`](https://www.npmjs.com/package/@boomi/embedkit-cdn) ← **this package** | Any website — drop in a `<script>` tag, no build step needed |

---

## What Is This Package?

This package contains the pre-built CDN distribution files for EmbedKit:

| File | Description |
|------|-------------|
| `embedkit-cdn.umd.cjs` | UMD bundle — works in all browsers via a `<script>` tag |
| `embedkit-cdn.css` | Required stylesheet |

React and ReactDOM are bundled in — nothing else is required on the host page.

The files are served via public CDN providers:

- **jsDelivr:** `https://cdn.jsdelivr.net/npm/@boomi/embedkit-cdn/`
- **unpkg:** `https://unpkg.com/@boomi/embedkit-cdn/`

---

## Quick Start

Add the following to any HTML page, just before `</body>`:

```html
<!-- 1. EmbedKit Stylesheet -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@boomi/embedkit-cdn/embedkit-cdn.css" />

<!-- 2. Configure the embed -->
<script>
  window.BoomiEmbed = {
    publicToken: "pk_xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
    agentId:     "project_xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
    mountId:     "boomi-agent",
    serverBase:  "https://api.boomi.space/api/v1"
  };
</script>

<!-- 3. Load the bundle -->
<script src="https://cdn.jsdelivr.net/npm/@boomi/embedkit-cdn/embedkit-cdn.umd.cjs" async></script>

<!-- 4. Mount target -->
<div id="boomi-agent"></div>
```

The agent UI will automatically initialize and render inside the `boomi-agent` div.

---

## Configuration

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `publicToken` | `string` | Yes | The `pk_...` public token from your project in Admin Console |
| `agentId` | `string` | Yes | The project ID from Admin Console |
| `serverBase` | `string` | Yes | EmbedKit API base URL: `https://api.boomi.space/api/v1` |
| `mountId` | `string` | No | ID of the `<div>` to mount into. Defaults to `"boomi-agent"` |
| `userId` | `string` | No | Identifier for the current user (for session tracking / analytics) |
| `autoInit` | `boolean` | No | Set to `false` to disable automatic initialization. Default: `true` |

---

## Getting a Public Token

Tokens and projects are managed through the EmbedKit Admin Console at [admin.boomi.space](https://admin.boomi.space). See the full setup guide in the [EmbedKit documentation](https://github.com/OfficialBoomi/embedkit).

---

## Documentation

Full documentation for EmbedKit — including the CDN configuration guide, project setup, embed types, theming, and API reference — is available in the main repository:

**[github.com/OfficialBoomi/embedkit](https://github.com/OfficialBoomi/embedkit)**

---

## Content Security Policy

If your site uses a CSP, add the following directives:

```
script-src  'self' https://cdn.jsdelivr.net;
style-src   'self' https://cdn.jsdelivr.net;
connect-src 'self' https://api.boomi.space;
```
