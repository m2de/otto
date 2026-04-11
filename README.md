<div align="center">

# Otto

**A desktop dashboard for managing Claude agent sessions.**

Less noise. More visibility. Full control.

[Download](#download) · [Features](#features) · [Pricing](#pricing) · [Getting Started](#getting-started)

<!-- Replace with actual screenshot before launch -->
<!-- ![Otto Dashboard](docs/assets/hero-screenshot.png) -->

</div>

---

## What is Otto?

CLI agents are noisy. Scrolling chat logs make it hard to see what actually happened — which files changed, what decisions were made, how much it cost. When you're running multiple agents across different projects, keeping track of everything through terminal windows becomes a constant drain on your attention.

Otto replaces that with a dashboard that surfaces everything at a glance. Session status, file diffs, tool usage, costs, tasks, and context usage — all visible without scrolling through conversation history. It's a power user tool: less noise, more visibility, less effort to stay on top of what your agents are doing.

On top of that, Otto provides deep GitHub integration — launch agents directly from issues, PRs, and discussions, manage worktrees, and track CI runs. Plus webhook and cron automations that trigger agent sessions automatically, so your agents can respond to events without you being there.

Otto works with the Anthropic API, Amazon Bedrock, Google Vertex AI, and Azure AI Foundry. If you're on Bedrock, Vertex, or Azure and don't have access to Claude's native apps, Otto gives you the same experience regardless of your provider.

## Features

### Multi-Session Management

- Launch and monitor multiple agent sessions simultaneously from a single dashboard
- Fleet-level inbox with status grouping: working, blocked, done, error, idle
- "Needs action" view surfaces sessions that require human input
- Session pinning, forking, renaming, and history replay
- Filter and search across all sessions

### Real-Time Transcripts

- Live streaming transcripts with rich content types — code, files, tool calls, thinking blocks
- "Now Playing" header showing the agent's current activity at a glance
- File checkpoint and rewind system with visual diff preview before confirming
- Transcript annotations — highlight text and attach comments as context for the next prompt

### Quick Chat

- Floating "btw" panel for quick, read-only questions about your codebase — no need to create a full session
- Pre-warmed for near-instant responses
- Open with `Cmd+.` / `Ctrl+.`, supports multi-turn conversations

### Agent Control

- Granular session configuration: permission modes, thinking budgets, cost limits, turn limits, sandbox mode, tool restrictions, structured output, and more
- Interactive permission and plan approval with visual previews
- Follow-up message queueing while agents are working
- Prompt suggestions, slash command autocomplete, and image attachments
- Change model, permission mode, and reasoning effort mid-session

### Visual Previews

- When Claude presents options or asks questions, Otto renders fully interactive HTML previews directly in the dashboard
- See UI mockups, architecture diagrams, and design options as actual rendered visuals — not markdown descriptions
- Quickly verify your agent understands the task before it starts building

### Git & GitHub

- Built-in git panel: branch status, pull, push, fetch, stash, commit history
- GitHub panel with Issues, Pull Requests, Discussions, CI Runs, and Tags
- One-click "Launch Agent" from any GitHub item — automatically creates a worktree
- Full worktree lifecycle management with batch operations and safety checks
- Self-assignment on issues, label filtering, fuzzy search

### Automation

- **Webhook automations** — markdown-based rules triggered by GitHub events, with event/action/repo/sender matching and template expansion
- **Cron automations** — scheduled agent sessions using cron expressions, with template expansion and manual trigger support
- Live webhook event feed with one-click automation creation from any event
- Per-automation session configuration (model, permissions, worktree, sandbox, budget, and more)

### Fleet Management

- Inbox panel with a fleet-level overview of all running agents
- Status grouping: working, blocked, done, error, idle — with counts
- "Needs action" section groups all sessions waiting for human input
- Quick access to recently completed sessions

### Multi-Project Support

- Project picker with automatic git repository scanning
- Project rail for switching between repositories
- Multi-repo projects — a single project can contain multiple git repositories

### Built-In Tools

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

## Pricing

<div align="center">

**One plan. Every feature. No tiers.**

### £25/month or £200/year

</div>

- Every feature included from day one — no upsells, no feature gating
- **14-day free trial** — no payment details required
- **30-day money-back guarantee** — no questions asked

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
