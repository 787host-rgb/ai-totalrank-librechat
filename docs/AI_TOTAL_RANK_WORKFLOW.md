# AI Total Rank Workflow

## Current repository

Repository:

```text
787host-rgb/ai-totalrank-librechat
```

This is the clean AI Total Rank fork of LibreChat.

## Current status

Completed and merged:

```text
PR #1 - Browser title and metadata changed to AI Total Rank
PR #2 - Branding audit document added
PR #3 - PWA manifest name changed to AI Total Rank
PR #4 - Startup/login browser title fallback changed to AI Total Rank
PR #5 - Agent attribution label changed to AI Total Rank
PR #6 - Auth logo alt fallback changed to AI Total Rank
PR #7 - Added small AI Total Rank librechat.yaml config
```

Not done yet:

```text
Logo replacement
Favicon replacement
Full visible text audit from local search
Custom Docker build validation
Server deployment
Cloudflare Tunnel connection
```

## Important boundary

Do not touch the old XCloud LibreChat install yet.

Do not touch Cloudflare Tunnel yet.

Do not touch Valeria repositories or files.

The old live app can stay as-is while this clean fork is prepared.

## Recommended order from here

```text
1. Clone this repository locally or open it in a coding workspace
2. Run a local text search for remaining visible LibreChat references
3. Keep safe package/internal names unchanged
4. Replace logo and favicon only after approved AI Total Rank assets exist
5. Validate local install/build
6. Prepare custom Docker build from this repository
7. Deploy to XCloud only after the build is proven
8. Connect Cloudflare Tunnel at the end
```

## Local clone command

```bash
git clone https://github.com/787host-rgb/ai-totalrank-librechat.git
cd ai-totalrank-librechat
```

## First local audit commands

Run these after cloning:

```bash
grep -R "LibreChat" -n client api packages --exclude-dir=node_modules --exclude-dir=dist --exclude-dir=build
```

Also check lowercase references:

```bash
grep -R "librechat" -n client api packages --exclude-dir=node_modules --exclude-dir=dist --exclude-dir=build
```

Do not automatically replace everything.

Classify each result as one of these:

```text
Safe visible branding
Needs caution
Internal package/import name
Docker/build/deployment reference
Upstream attribution/documentation
Should not change yet
```

## Safe next targets

Likely safe next areas:

```text
client/public/assets/logo.svg
client/public/assets/favicon-16x16.png
client/public/assets/favicon-32x32.png
client/public/assets/apple-touch-icon-180x180.png
client/public/assets/icon-192x192.png
client/public/assets/maskable-icon.png
Visible frontend fallback strings found by local grep
```

Only replace visual assets after the user approves the final AI Total Rank logo/favicon.

## Things to avoid for now

Do not rename packages such as:

```text
@librechat/client
@librechat/api
librechat-data-provider
```

Do not casually edit these without a deployment plan:

```text
docker-compose.yml
deploy-compose.yml
MONGO_URI values
container_name values
official registry image references
```

Do not do a global find-and-replace of `LibreChat`.

## Docker direction

The final branded product should be built from this fork's source code.

Target direction:

```text
AI Total Rank fork -> custom build -> branded container -> XCloud server -> Cloudflare Tunnel
```

Avoid relying on the official prebuilt LibreChat image as the final branded product.

## Notes

The repository now has both:

```text
AGENTS.md
docs/AI_TOTAL_RANK_BRANDING_AUDIT.md
docs/AI_TOTAL_RANK_WORKFLOW.md
```

These should guide the next local/VS Code/Codex work.