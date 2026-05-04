# AI Total Rank Branding Audit

## Purpose

This document tracks the first branding audit for the AI Total Rank fork of LibreChat.

The goal is to make the product feel like AI Total Rank while keeping the LibreChat fork stable and maintainable.

## Current product target

- Product name: AI Total Rank
- Target domain: ai.totalrank.pro
- Repository: 787host-rgb/ai-totalrank-librechat
- Upstream: danny-avila/LibreChat

## Rule

Do not blindly replace every occurrence of `LibreChat`.

Some references are safe visible branding. Others are internal identifiers, Docker image references, MongoDB database names, package namespaces, upstream attribution, or documentation references.

## Already changed

### PR #1

Changed browser-facing metadata in `client/index.html`:

- `<title>LibreChat</title>` -> `<title>AI Total Rank</title>`
- Meta description changed from LibreChat text to AI Total Rank text

This was safe because it did not touch authentication, Docker, database, model providers, server deployment, or Cloudflare Tunnel.

## Safe to brand soon

These are user-visible or product-facing areas and should be changed in small PRs:

### `client/vite.config.ts`

PWA manifest currently uses:

```ts
name: 'LibreChat'
short_name: 'LibreChat'
```

Recommended change:

```ts
name: 'AI Total Rank'
short_name: 'AI Total Rank'
```

This affects installed app/PWA naming.

### `.env.example`

UI section includes:

```env
APP_TITLE=LibreChat
HELP_AND_FAQ_URL=https://librechat.ai
```

Recommended later change:

```env
APP_TITLE=AI Total Rank
HELP_AND_FAQ_URL=
```

or point `HELP_AND_FAQ_URL` to an AI Total Rank support page when one exists.

### Visible auth/login/app-shell copy

Need deeper file search once GitHub indexing is ready or once the repo is opened in VS Code/Codex.

Look for visible strings such as:

- `by LibreChat`
- `LibreChat Code Interpreter API`
- `Custom connectors are not verified by LibreChat`
- login screen logo/name references
- sidebar/app shell references

## Needs caution

These may be changed later, but only after checking impact:

### Root `package.json`

Current metadata includes:

```json
"name": "LibreChat"
"repository": "git+https://github.com/danny-avila/LibreChat.git"
"bugs": "https://github.com/danny-avila/LibreChat/issues"
"homepage": "https://librechat.ai/"
```

Do not change all of these immediately. Some are upstream references and may help future maintenance.

### `client/package.json`

Current metadata includes:

```json
"name": "@librechat/frontend"
```

Do not rename package namespaces yet. This may break imports, workspace references, or package resolution.

### Dependencies using LibreChat names

Examples:

```json
"@librechat/client": "*"
"librechat-data-provider": "*"
```

Do not rename these until there is a dedicated package-refactor plan.

## Do not change yet

### Docker Compose default file

`docker-compose.yml` contains:

```yaml
container_name: LibreChat
image: registry.librechat.ai/danny-avila/librechat-dev:latest
MONGO_URI=mongodb://mongodb:27017/LibreChat
```

Do not change this in a branding PR.

Reason: Docker and database names affect deployment behavior and existing data paths.

### `deploy-compose.yml`

Contains:

```yaml
image: registry.librechat.ai/danny-avila/librechat-dev-api:latest
container_name: LibreChat-API
container_name: LibreChat-NGINX
MONGO_URI=mongodb://mongodb:27017/LibreChat
```

Do not change until we prepare the custom build strategy.

### RAG image references

The RAG service currently references official LibreChat registry images. Do not change until custom deployment is planned.

## Custom build direction

The final branded product should not depend on the official prebuilt LibreChat app image as the main app image.

Target:

```text
AI Total Rank repository -> custom Docker build -> branded app container -> XCloud deployment -> Cloudflare Tunnel
```

Avoid:

```text
official LibreChat image -> superficial overrides -> fragile branding
```

## Recommended next PR sequence

1. PWA manifest title branding
2. `.env.example` UI title branding
3. Visible login/app-shell string audit and minimal replacement
4. Logo/favicon asset replacement
5. Custom Docker build plan using existing `Dockerfile.multi`
6. Server deployment preparation
7. Cloudflare Tunnel connection only after local/server validation

## Notes for Codex

Codex should treat this as the current branding map.

Before changing files, Codex should explain:

- Which category each file belongs to
- Whether it is visible branding or internal infrastructure
- How to test the result
- Why the change is safe

Do not touch Valeria repositories or files.
