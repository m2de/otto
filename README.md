<div align="center">

# Otto

<img src="docs/assets/logo.png" width="512" alt="Otto logo" />

**A desktop dashboard for managing Claude agent sessions.**

Less noise. More visibility. Full control.

[Download](#download) · [Features](#features) · [Beta Access](#beta-access) · [Getting Started](#getting-started)

<!-- Replace with actual screenshot before launch -->
<!-- ![Otto Dashboard](docs/assets/hero-screenshot.png) -->

</div>

---

## What is Otto?

Otto is a desktop dashboard for professional developers who run multiple Claude agents simultaneously. It replaces noisy terminal logs with a clean, real-time overview — session status, file diffs, costs, and tasks all visible at a glance. Less scrolling, more doing.

It's built around GitHub. Launch agents from issues, PRs, and discussions, manage worktrees, and automate sessions with webhooks and cron triggers — so your agents can respond to events without you being there.

Otto works with the Anthropic API, Amazon Bedrock, Google Vertex AI, and Azure AI Foundry. If you're on Bedrock, Vertex, or Azure and don't have access to Claude's native apps, Otto gives you a first-class experience regardless of your provider.

## Features

### Multi-Session Management

- Launch and monitor multiple agent sessions simultaneously from a single dashboard
- Stage overview with tiered session grouping: Needs Attention, Working, Idle, and Inactive
- Sessions requiring human input are surfaced at the top automatically
- Session pinning, forking, renaming, and history replay
- Filter and search across all sessions
- Agent orchestration — agents can spawn child sessions to delegate work and send messages between sessions to coordinate

### Real-Time Transcripts

- Live streaming transcripts with rich content types — code, files, tool calls, thinking blocks, memory recalls
- "Now Playing" header showing the agent's current activity at a glance
- File checkpoint and rewind system with visual diff preview before confirming
- Transcript annotations — highlight text and attach comments as context for the next prompt

### Session Views

- Three alternative session visualisations beyond the standard dashboard: Neural Pulse, Mission Timeline, and Cockpit HUD
- **Neural Pulse** — living organism canvas showing causal relationships between prompts, thinking, and tool calls as an interactive force-directed graph, zoomable and pannable, with sub-agents as integrated branches
- **Mission Timeline** — mission control layout with parallel activity tracks, draggable minimap, and click-to-inspect detail panel
- **Cockpit HUD** — flight instrument aesthetic with context gauge, tool radar, cost readouts, and transcript message cycling
- View picker toggle with persistent selection across sessions

### Quick Chat

- Floating "btw" panel for quick, read-only questions about your codebase — no need to create a full session
- Pre-warmed for near-instant responses
- Open with `Cmd+.` / `Ctrl+.`, supports multi-turn conversations

### Agent Control

- Granular session configuration: permission modes, thinking budgets, cost limits, turn limits, sandbox mode, tool restrictions, structured output, and more
- Interactive permission and plan approval with visual previews
- Auto-approval mode — safe tool requests are approved automatically with confidence scoring; risky or uncertain requests still surface for manual review
- Follow-up message queueing while agents are working
- Prompt suggestions, slash command autocomplete, and image attachments
- Hooks management — view, create, edit, and delete hooks across user, project, and local settings with full lifecycle event coverage
- Provider profiles — configure and switch between API providers, with environment isolation and auto-detection of existing credentials
- Change model, permission mode, and reasoning effort mid-session

### Visual Previews

- When Claude presents options or asks questions, Otto renders fully interactive HTML previews directly in the dashboard
- See UI mockups, architecture diagrams, and design options as actual rendered visuals — not markdown descriptions
- Quickly verify your agent understands the task before it starts building

### In-App Browser

- Agents can open web pages directly inside the session panel for you to review — no separate window needed
- Resizable browser panel with device viewport presets (mobile, tablet, desktop), fullscreen expand, and toolbar controls
- Annotation overlay lets you highlight elements on the page, add comments, and send structured feedback back to the agent
- Element screenshots and selectors are included in the feedback so the agent knows exactly what you're referring to

### Git & GitHub

- Interactive branch visualisation with ahead/behind indicators relative to the default branch
- Dedicated branch detail pages with Changes (diff viewer), Commits (log), and Status (PR, CI, linked sessions) tabs
- Launch agents directly from any branch detail page — automatically creates a worktree
- Worktree overview showing linked agent sessions per worktree
- GitHub panel with Issues, Pull Requests, Discussions, CI Runs, and Tags
- One-click "Launch Agent" from any GitHub item — automatically creates a worktree
- Full worktree lifecycle management with batch operations and safety checks
- Self-assignment on issues, label filtering, fuzzy search

### Automation

- Dedicated **Automations** tab with structured editors for cron schedules and GitHub webhook rules — no need to hand-edit files
- Cron editor with schedule presets and a live next-fires preview, so you can see when your automation will actually run
- Webhook match builder with event/action chips, repo/sender/label filters, and payload matchers — plus a Form/Raw toggle for power users
- Persistent event feed and Insights panel showing top event types, hourly volume, and one-click "Create automation" suggestions for high-volume events
- Per-automation session configuration (model, permissions, worktree, sandbox, budget, and more)

### Multi-Project Support

- Project picker with automatic git repository scanning
- Quick-switch navigation between repositories
- Multi-repo projects — a single project can contain multiple git repositories

### Plugins & Marketplace

- Unified browse view across all configured marketplaces — installed and available plugins side by side, no dropdown prerequisite
- Dedicated plugin detail pages with author, repository, licence, and keywords surfaced from marketplace manifests
- Enable, disable, and configure plugins at user, project, or local level — inline from the detail page
- Add marketplace sources from GitHub, npm, git, URL, file, or directory
- Trust and security controls: strict mode, blocked sources, and custom trust messages

### Built-In Tools

- In-app feedback tool — annotate UI elements and submit bug reports directly from the dashboard
- Automatic updates with in-app download and restart
- Detailed context usage breakdown with token counts by category
- SDK recording and debugging tools
- Mobile-responsive layout

## Download

> **Coming soon.** Otto is currently in development. Watch this repo to be notified when downloads are available.

<!-- Replace with actual download links before launch:
| Platform | Download |
|----------|----------|
| macOS (Apple Silicon) | [Otto-x.x.x-arm64.dmg](#) |
| macOS (Intel) | [Otto-x.x.x-x64.dmg](#) |
| Windows | [Otto-x.x.x-setup.exe](#) |
| Linux | [Otto-x.x.x.AppImage](#) |
-->

## Getting Started

1. **Download and install** Otto from the links above
2. **Open Otto** — the dashboard opens automatically
3. **Select a project** — Otto scans for git repositories and lets you pick one
4. **Create a session** — configure permissions, thinking budget, and tools, then launch your first agent
5. **Watch it work** — follow the real-time transcript, approve permissions when asked, and queue follow-up messages

## Beta Access

Otto is currently in closed beta. You can download and install it, but you'll need a licence key to use it.

If you'd like to try Otto, [open a discussion](https://github.com/m2de/otto/discussions) or reach out directly to request access.

> **Note:** Otto is the dashboard. You bring your own API access — Anthropic API, Amazon Bedrock, Google Vertex AI, or Azure AI Foundry.

## Requirements

- macOS 12 or later (Apple Silicon or Intel)
- One of the following:
  - An [Anthropic API key](https://console.anthropic.com/)
  - [Amazon Bedrock](https://aws.amazon.com/bedrock/) access with Claude enabled
  - [Google Vertex AI](https://cloud.google.com/vertex-ai) access with Claude enabled
  - [Azure AI Foundry](https://ai.azure.com/) access with Claude enabled

## Support

- **Bug reports** — [Open an issue](https://github.com/m2de/otto/issues/new?template=bug_report.md)
- **Feature requests** — [Open an issue](https://github.com/m2de/otto/issues/new?template=feature_request.md)
- **Questions & discussion** — [Start a discussion](https://github.com/m2de/otto/discussions)

## Links

- [Claude documentation](https://docs.anthropic.com/)
- [Anthropic](https://anthropic.com)

---

<div align="center">

Made by [m2de](https://github.com/m2de)

</div>
