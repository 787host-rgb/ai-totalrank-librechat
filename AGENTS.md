# AGENTS.md — AI Total Rank LibreChat Fork

## Project identity

This repository is a branded fork of LibreChat for the AI Total Rank product.

- Product name: AI Total Rank
- Target domain: ai.totalrank.pro
- Upstream source: danny-avila/LibreChat
- Repository owner: 787host-rgb
- Repository name: ai-totalrank-librechat

The goal is to create a clean, maintainable, branded LibreChat fork. This project must not be treated as a quick patch over a running container or a temporary server edit.

## Non-negotiable boundaries

Do not touch, reference, edit, or migrate anything from the Valeria project.

Never make changes to any repository named or related to:

- valeria-live-stable
- valeria-lab
- valeria.chat
- Valeria

This repository is only for AI Total Rank.

## Work style

Make small, reviewable changes.

Prefer one focused pull request per task.

Do not perform large rewrites unless the user explicitly approves the scope.

Do not redesign the full application in one pass.

Do not change authentication, database behavior, provider logic, billing logic, Docker architecture, or deployment assumptions unless specifically requested.

Do not remove upstream functionality just because it contains LibreChat internals. First classify whether it is visible branding, legal attribution, code namespace, package metadata, Docker behavior, or documentation.

## Branding goal

Visible product branding should become AI Total Rank.

Priority targets:

- Browser title
- Public metadata
- Favicon and app icons
- Visible logo
- Visible app name
- Login and welcome screens
- Sidebar/app shell visible labels
- PWA/manifest labels if present
- Any user-facing LibreChat text that makes the product feel unbranded

Do not blindly replace every occurrence of `LibreChat` in code. Some references may be required for upstream compatibility, package names, namespaces, legal notices, or documentation.

## Fork strategy

This project should build from this repository's source code.

Do not rely on the official prebuilt LibreChat image as the final branded product.

Target direction:

```text
AI Total Rank repository -> custom build -> branded container -> server deployment
```

Avoid:

```text
official LibreChat image -> superficial override -> fragile branding
```

## Server and Cloudflare boundary

Do not touch server deployment, XCloud, Nginx, Docker production containers, or Cloudflare Tunnel unless the user explicitly asks.

Current intended order:

1. Prepare the fork in GitHub
2. Add project rules
3. Audit visible LibreChat branding
4. Apply minimal branding changes
5. Validate local/build behavior
6. Prepare controlled Docker deployment
7. Move to XCloud server
8. Connect Cloudflare Tunnel at the end

The Cloudflare Tunnel is not part of early development. It should only be connected after the branded fork is validated.

## Codex usage rules

Codex may help with auditing, code navigation, small edits, and PR preparation.

Codex must not decide the full architecture by itself.

Before changing files, Codex should explain:

- Which files it plans to change
- Why those files matter
- Whether the change is visible branding, build behavior, documentation, or deployment
- How to test the result

## First audit task

The first technical task should be an audit only.

Find references to:

- LibreChat
- librechat
- LIBRECHAT
- danny-avila
- app title metadata
- favicon/logo assets
- manifest/PWA name
- login/welcome branding

Classify findings into:

1. Safe to brand now
2. Needs caution
3. Should not change yet
4. Legal/upstream attribution
5. Docker/build related

Do not modify files during the audit.

## Quality bar

The branded product must feel intentional, not patched.

A user opening ai.totalrank.pro should see AI Total Rank, not a half-renamed LibreChat install.

Maintain stability first. Branding changes should not break chat, login, Docker, or provider configuration.
