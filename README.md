# EventHive: Event CRM — Deal Pipeline

> Lightweight deal pipeline for event sales teams. Track sponsor prospects, exhibitor outreach, and partnership deals with staleness alerts, deal scoring, and weighted pipeline value.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Part of EventHive](https://img.shields.io/badge/Part%20of-EventHive-orange)](https://eventhive.io)

![Screenshot](thumbnail.png)

## Quick Start

### Browser Mode (no install)

1. Download the [latest release](../../releases/latest) or clone this repo
2. Open `tool.html` in any modern browser
3. Start using it — data saves automatically (requires EventHive hosting for full cloud sync)

### Also Available on EventHive

This tool is available on [EventHive](https://eventhive.io) — the free platform for event professionals. On EventHive, your data syncs across devices, integrates with your other tools, and includes AI assistance from Erleah.

---

## Features

- Kanban pipeline: Prospect → Qualified → Proposal → Negotiation → Won/Lost
- Deal scoring with weighted probability
- Staleness alerts when deals go cold
- Contact management with activity log
- Pipeline value dashboard with forecasting
- Export to CSV and JSON

---

## Customising This Tool

This tool was built using AI-assisted development ("vibe coding").
To customise it for your needs:

1. **Fork this repo** (click the Fork button above)
2. **Clone your fork** locally
3. **Read the [AI Coding Docs](https://github.com/Visual-Hive/ai-coding-docs)** — our methodology for building tools like this with AI
4. **Open in your AI editor** (Claude Code, Cursor, Copilot, etc.)
   - The `.clinerules` file gives your AI assistant context about this tool
   - For Claude Code: run `claude` and the rules load automatically
5. **Modify, test, deploy** — it's just HTML, CSS, and vanilla JS

> **Tip:** The `manifest.json` file defines the configuration schema.
> If you add new configurable options, update it so your tool works with the EventHive platform's config editor.

---

## Data Storage

| Mode | Where | Persistence |
|------|-------|-------------|
| Browser | localStorage (fallback) | Until browser data cleared |
| EventHive | Cloud database (PostgreSQL) | Synced across devices |

This tool stores data in `eventhive_event_{eventSlug}_sales`. In cloud-hosted mode on EventHive, data is synced to a PostgreSQL database.

---

## Related Tools

- [Sponsor Deliverables Tracker](https://github.com/Visual-Hive/eventhive-tool-sponsor-deliverables) — won deals flow into Sponsor Deliverables
- [Exhibitor Manager](https://github.com/Visual-Hive/eventhive-tool-exhibitor-manager) — booked exhibitors flow into Exhibitor Manager

---

## Contributing

PRs welcome! Please read the [Contributing Guide](https://github.com/Visual-Hive/eventhive-tools/blob/main/CONTRIBUTING.md) first.

---

## License

MIT — free to use, modify, and distribute.

Built by [Visual Hive](https://visualhive.io) as part of the [EventHive](https://eventhive.io) open-source toolkit.

---

## 🐳 Self-Hosting

Run this tool on your own infrastructure using Docker Compose. Your data stays on your servers.

### Prerequisites
- [Docker Desktop](https://docs.docker.com/get-docker/) (or Docker Engine + Compose V2)
- ~512 MB RAM

### Quick Start

```bash
# 1. Clone this repo
git clone https://github.com/Visual-Hive/eventhive-tool-event-crm.git
cd eventhive-tool-event-crm

# 2. Run the setup script — it handles .env creation, optional password, and Docker build
bash self-hosted/setup.sh

# 3. Open the tool in your browser
open http://localhost:3000
```

### Manual Setup (without the script)

```bash
cd self-hosted
cp .env.example .env
# Edit .env to set SESSION_SECRET, optional PASSWORD_HASH, etc.
docker compose up -d --build
```

### Setting a Login Password

By default the tool runs in open-access mode (fine for local use).
To add password protection:

```bash
cd self-hosted
npm install
npm run hash-password yourpassword   # copy the $2b$... hash
# Paste into .env:  PASSWORD_HASH=<hash>
docker compose restart app
```

### Configuration (.env)

| Variable | Default | Description |
|---|---|---|
| `PORT` | `3000` | HTTP port |
| `SESSION_SECRET` | *(required)* | Random string for signing sessions |
| `PASSWORD_HASH` | *(empty = open)* | bcrypt hash of your access password |
| `TOOL_TITLE` | `Event CRM` | Title shown inside the tool |
| `PRIMARY_COLOR` | `#6366f1` | Branding colour (hex) |

### Data Storage

All data is stored in a PostgreSQL database inside the Docker volume `db_data`.

**Backup:**
```bash
docker compose -f self-hosted/docker-compose.yml exec db pg_dump -U tool tooldb > backup.sql
```

**Restore:**
```bash
cat backup.sql | docker compose -f self-hosted/docker-compose.yml exec -T db psql -U tool tooldb
```

---

> This self-hosted backend is API-compatible with [EventHive](https://eventhive.io), so you can migrate your data to the hosted version at any time using the tool's built-in export/import feature.
