# Start Here — AI Total Rank Fork

## Repository

```text
787host-rgb/ai-totalrank-librechat
```

This is a branded LibreChat fork for AI Total Rank.

## Read first

Before changing files, read these documents in this order:

```text
AGENTS.md
docs/AI_TOTAL_RANK_BRANDING_AUDIT.md
docs/AI_TOTAL_RANK_WORKFLOW.md
```

## Current state

The repo already has the first safe branding layer merged:

```text
Browser title and metadata
PWA manifest name
Startup/login title fallback
Auth logo alt fallback
Agent attribution label
Small AI Total Rank librechat.yaml
Branding audit document
Workflow document
```

## Do not touch yet

Do not touch these until the user explicitly moves into deployment/build work:

```text
XCloud server
Cloudflare Tunnel
Nginx
Production containers
Production .env files
MONGO_URI values
Docker image references
Container names
Valeria repositories or files
```

## Next useful tasks

### 1. Local visible branding audit

Run local searches and classify the remaining references.

```bash
grep -R "LibreChat" -n client api packages --exclude-dir=node_modules --exclude-dir=dist --exclude-dir=build

grep -R "librechat" -n client api packages --exclude-dir=node_modules --exclude-dir=dist --exclude-dir=build
```

Classify each result as:

```text
Safe visible branding
Needs caution
Internal package/import name
Docker/build/deployment reference
Upstream attribution/documentation
Should not change yet
```

Do not do a global find-and-replace.

### 2. Validate the new YAML config

Confirm `librechat.yaml` is loaded correctly by the app when running from source.

Current file:

```text
librechat.yaml
```

It is intentionally small and brand-focused.

### 3. Prepare visual asset replacement plan

Only replace logo and favicon after approved AI Total Rank assets exist.

Likely asset targets:

```text
client/public/assets/logo.svg
client/public/assets/favicon-16x16.png
client/public/assets/favicon-32x32.png
client/public/assets/apple-touch-icon-180x180.png
client/public/assets/icon-192x192.png
client/public/assets/maskable-icon.png
```

### 4. Build strategy later

The final branded product should be built from this fork, not from the official prebuilt LibreChat image.

Target:

```text
AI Total Rank fork -> custom build -> branded container -> XCloud server -> Cloudflare Tunnel
```

## Working rule

Keep each change small and reviewable.

Open one focused pull request per task.

Do not change architecture unless the user explicitly approves it.
