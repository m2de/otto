# Changelog

All notable changes to Otto will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added

- Stage — tiered session overview (Needs Attention, Working, Idle, Inactive) replacing the fleet inbox for clearer prioritisation at a glance
- Git dashboard — interactive branch spine with ahead/behind indicators and dedicated branch detail pages (changes, commits, status)
- Auto-approval — sessions in "auto" permission mode intelligently approve safe tool requests, showing confidence and reasoning in the timeline; uncertain or risky requests still prompt for manual approval
- Automations tab — top-level home for cron and webhook automations, with structured form editors, live event feed, and Insights showing top event types, recent volume patterns, and one-click suggestions for frequent events
- Hooks tab — top-level home for hook management, with structured editors, a test panel for dry-run and live execution against synthesised payloads, recent-fires strip showing real execution outcomes per hook, enable/disable without deletion, and inline rename
- Agent orchestration — sessions can now spawn child sessions and send messages to one another, enabling one agent to delegate work, coordinate with peers, and wait for results before continuing

### Fixed

- Environment isolation — Otto no longer leaks a `PORT` variable into agent sessions, which previously caused user tools (Express, Next.js, test harnesses) to bind to the wrong port
- Worktrees with uncommitted changes or unpushed commits are no longer deleted when a session stops — only clean worktrees are auto-cleaned
- Cost tracking — the Stage header's "today" figure and per-repo totals are now sourced from the provider's reported cost rather than estimated from token counts, so Bedrock, Vertex, and Azure users see accurate numbers instead of a Sonnet-priced approximation

### Improved

- Session auto-naming — unnamed sessions are automatically titled from the plan heading when a plan is approved
- Navigation — streamlined icon rail layout with direct routing to Stage, Repo, Worktrees, GitHub, Plugins, and Config
- Sub-agent modal — live metadata updates, conversation auto-scroll with sticky scroll-to-bottom, and full response display without truncation
- Auto-updater — pre-release channel support with tray toggle; RC versions automatically receive pre-release updates
- Worktrees — gitignored files listed in `.worktreeinclude` (e.g. `.env`) are now automatically copied into Otto-created worktrees
- Permissions settings — unified rule-centric view across user, project, and local scopes, with conflict detection (duplicates, allow/deny clashes, wildcard shadowing), a guided Add Rule wizard, scope-chip move/duplicate, and bulk select with drag-and-drop
- Plugins — unified browse view across all configured marketplaces (no per-marketplace dropdown), dedicated detail pages with author, repository, licence, and keywords, inline scope management, and visual polish matching the Stage and Repo pages
- Automations editing — cron and webhook rules now have structured editors with live schedule previews and match-builder chips; the Form/Raw toggle keeps the underlying file accessible for power users
- Stage cards — per-session cost is now shown directly on every card (Needs Attention, Working, Inactive), so you can see spend per session at a glance without opening it
- Project tabs — drag to reorder projects in the header; the order is remembered across reloads, and each project's dot colour stays stable when you rearrange them

## [0.4.0] - 2026-04-24

### Added

- Command Centre — three alternative session views (Neural Pulse, Mission Timeline, Cockpit HUD) with floating action bar and shared modal orchestration
- Provider Profiles — configure and switch between API providers from within the dashboard, with environment isolation and auto-detection of existing credentials
- Transcript tool activity toggle — show or hide tool calls, file reads, searches, and hooks to reduce noise in the live transcript

### Fixed

- Sub-agent activity no longer leaks into the main transcript — the "Hide sub-agents" toggle works correctly
- Annotation tool keyboard events no longer leak into the host page — typing in the feedback textarea works correctly

### Improved

- Git panel — overhauled into a developer command centre with branch switcher (fuzzy search), sync status bar, staged/modified/untracked file grouping, inline diff expansion, and rebase support
- Neural Pulse activity graph — force-directed layout with collision detection, directional edge particles, canvas rendering for scale, sub-agents as integrated branches
- In-app browser — device viewport presets (mobile, tablet, desktop), fullscreen expand/collapse, and improved page rendering
- In-app feedback tool — annotate UI elements and submit bug reports directly from the dashboard
- Sub-agent improvements — colour-coded agent types, modal detail view, and clickable sidebar entries
- Hooks management — view, create, edit, and delete hooks across user, project, and local settings levels

## [0.3.0] - 2026-04-16

### Added

- Automatic updates — Otto checks for new versions in the background and prompts to restart when ready
- Plugins & Marketplace panel for browsing, installing, and configuring plugins from marketplace sources
- Skill and slash command output now visible in transcripts
- Closed beta access model with free beta plan

### Fixed

- Session renames now persist through catchup replay
- Subagent status no longer goes stale after task updates
