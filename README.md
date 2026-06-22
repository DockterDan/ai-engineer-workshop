# AI Engineer Workshop: From Approval Loops to Autonomous Agents with Docker

A 90-minute hands-on workshop on Docker primitives for safe AI agent autonomy. Covers SBX (Docker Sandboxes), DHI (Docker Hardened Images), MCP, SBX Kits, cagent / Docker Agent multi-agent orchestration, and per-role capability isolation.

**Live URL:** _TODO: replace with the GitHub Pages URL once Pages is enabled (see "Hosting" below)_

## Context

Co-presented by Dan Ndombe and John Craft at the AI Engineer's World's Fair in San Francisco, June 29 – July 2, 2026.

The workshop walks attendees through eight steps, each pairing one Docker primitive with the kind of agent failure mode it prevents. Attendees leave with a sandboxed agent environment running on their own laptop, a hardened production image, and a multi-agent setup with per-role isolation.

## Viewing locally

The workshop is one self-contained HTML file. No build step. Just open `index.html` in any modern browser.

```bash
open index.html       # macOS
xdg-open index.html   # Linux
start index.html      # Windows
```

## Hosting

This repo is set up for GitHub Pages. After the first push:

1. Go to **Settings → Pages** in the GitHub repo.
2. Under **Source**, choose **Deploy from a branch**.
3. Set **Branch** to `main` and **Folder** to `/ (root)`.
4. Click **Save**.

GitHub will deploy within a minute or two. The live URL appears at the top of the Pages settings page. Edits go live on every push to `main`.

## Leaving feedback

Open an issue or comment on a PR. Style notes the workshop follows:

- No em dashes anywhere.
- No emojis.
- "MacOS" rather than "macOS".
- Lowercase `sbx` in commands and prose; uppercase `SBX` in section titles.
- Environment variables stay uppercase (e.g., `SBX_MCP_URL`).

## Repo structure

```
ai-engineer-workshop/
├── README.md              ← this file
├── index.html             ← the workshop, one self-contained HTML file
└── scripts/
    ├── reset-workshop.sh      ← soft reset: removes only what the workshop created
    └── uninstall-workshop.sh  ← full uninstall: removes Docker Desktop and all sbx state
```

## Scripts

Both scripts have `#!/usr/bin/env bash` shebangs, so they run regardless of the user's interactive shell. Standalone copies of these blocks also appear in the workshop's Wrap-up section so attendees can copy them straight from the page.

- **`scripts/reset-workshop.sh`** — Soft reset. Removes only the artifacts the workshop created: `sandbox-alpha`, the `pypi.org` deny and `fifa.com` allow rules, the Docker Hub and `dhi.io` logins, the workshop-built images, the `research-app` subdirectory, and the test files. Leaves `sbx`, Docker Desktop, your API key secrets, and the `~/workshop` umbrella directory alone. Safe for machines that had Docker or sbx in use before the workshop.

- **`scripts/uninstall-workshop.sh`** — Full uninstall. The nuclear option, designed for machines where Docker and sbx were installed specifically for this workshop. Removes Docker Desktop completely, every sandbox, every workshop artifact, all sbx state and Keychain credentials, and the entire `~/workshop` umbrella directory. Don't run this if you have other Docker or sbx work on the machine.

To execute either:

```bash
bash scripts/reset-workshop.sh        # or
bash scripts/uninstall-workshop.sh
```

The full uninstall prompts for confirmation before running.
# ai-engineer-workshop
# ai-engineer-workshop
