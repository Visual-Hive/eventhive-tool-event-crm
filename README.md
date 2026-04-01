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
