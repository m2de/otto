# Changelog

All notable changes to Otto will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added

- Memory tab — top-level home for Claude memory, unifying Instructions (CLAUDE.md hierarchy across user and project levels) and Learned (auto-memory) entries; view, edit, create, and delete at any level you own, with behaviour settings tucked into a collapsible section
- Stage — tiered session overview (Needs Attention, Working, Idle, Inactive) replacing the fleet inbox for clearer prioritisation at a glance
- Git dashboard — interactive branch spine with ahead/behind indicators and dedicated branch detail pages (changes, commits, status)
- Branch deletion — delete local branches from the branch detail page, with an optional "also delete remote" step when an upstream exists and an explicit acknowledgement when the branch has unmerged commits
- PR merge conflicts surfaced — conflicted pull requests in the GitHub panel are flagged with a red merge icon, and a one-click **Resolve conflicts** action launches a worktree agent that merges the base branch in, runs your checks, and pushes the fix without ever force-pushing
- Auto-approval — sessions in "auto" permission mode intelligently approve safe tool requests, showing confidence and reasoning in the timeline; uncertain or risky requests still prompt for manual approval
- Automations tab — top-level home for cron and webhook automations, with structured form editors, live event feed, and Insights showing top event types, recent volume patterns, and one-click suggestions for frequent events
- Automations safety — crons and webhooks are now off by default with per-repo on/off toggles in the header, so each repo opts in independently and nothing runs until you do (state resets on restart)
- Hooks tab — top-level home for hook management, with structured editors, a test panel for dry-run and live execution against synthesised payloads, recent-fires strip showing real execution outcomes per hook, enable/disable without deletion, and inline rename
- Agent orchestration — sessions can now spawn child sessions and send messages to one another, enabling one agent to delegate work, coordinate with peers, and wait for results before continuing
- Clear context — wipe a session's transcript and start fresh from the sidebar, or tick "Clear context" when approving a plan to begin implementation with a clean context window
- Background sub-agents — a **Background** button on each running sub-agent row (and in the sub-agent detail modal) lets a long-running sub-task continue on its own so the parent turn doesn't have to wait

### Fixed

- Environment isolation — Otto no longer leaks a `PORT` variable into agent sessions, which previously caused user tools (Express, Next.js, test harnesses) to bind to the wrong port
- Worktrees with uncommitted changes or unpushed commits are no longer deleted when a session stops — only clean worktrees are auto-cleaned
- Cost tracking — the Stage header's "today" figure and per-repo totals are now sourced from the provider's reported cost rather than estimated from token counts, so Bedrock, Vertex, and Azure users see accurate numbers instead of a Sonnet-priced approximation
- Inactive sessions no longer lose their cost badge when you open them — previously the recorded cost was visible in the list but vanished as soon as the session was opened
- Auto-approval — running multiple sessions concurrently no longer causes one session's earlier decisions to influence another's; each session now has its own classifier history, dropped when the session stops
- In-app browser — agent-triggered browser sessions now consistently open inline in the dashboard panel; previously a timing race could cause a separate browser window to appear instead
- Slash commands and skills are now available after resuming an idle session — previously the plugin list was not refreshed on resume, so skills disappeared until the session was restarted
- Model switching — the status-bar picker no longer shows a duplicate "Custom model" row alongside the resolved tier; switching model mid-session no longer leaves the session stuck on "Working"; and a failed model change now surfaces an inline error chip instead of silently doing nothing
- Effort picker — the in-session status-bar picker no longer hides "Extra High" mid-session; all five effort levels (Low, Medium, High, Extra High, Max) are now consistently available in both the new-session modal and the in-session picker
- GitHub tab no longer stalls on "Loading…" on first load or after a reconnect — counts now populate as soon as GitHub responds, and reconnecting repopulates the tab from cache instantly
- Stale "running" sub-agent rows are now cleaned up automatically — Otto reconciles against the agent runtime's view of active sub-agents on reconnect and at turn end, so ghost rows from dropped messages or replay gaps disappear on their own

### Improved

- Session auto-naming — unnamed sessions are automatically titled from the plan heading when a plan is approved, and a sparkle button next to any session title generates a fresh title from the conversation so far (handy when scope shifts mid-session)
- Navigation — streamlined icon rail layout with direct routing to Stage, Repo, Worktrees, GitHub, Plugins, and Config
- Sub-agent modal — live metadata updates, conversation auto-scroll with sticky scroll-to-bottom, and full response display without truncation
- Auto-updater — pre-release channel support with tray toggle; RC versions automatically receive pre-release updates
- Worktrees — gitignored files listed in `.worktreeinclude` (e.g. `.env`) are now automatically copied into Otto-created worktrees
- Permissions settings — unified rule-centric view across user, project, and local scopes, with conflict detection (duplicates, allow/deny clashes, wildcard shadowing), a guided Add Rule wizard, scope-chip move/duplicate, and bulk select with drag-and-drop
- Plugins — unified browse view across all configured marketplaces (no per-marketplace dropdown), dedicated detail pages with author, repository, licence, and keywords, inline scope management, and visual polish matching the Stage and Repo pages
- Automations editing — cron and webhook rules now have structured editors with live schedule previews and match-builder chips; the Form/Raw toggle keeps the underlying file accessible for power users
- Stage cards — per-session cost is now shown directly on every card (Needs Attention, Working, Inactive), so you can see spend per session at a glance without opening it
- Project tabs — drag to reorder projects in the header; the order is remembered across reloads, and each project's dot colour stays stable when you rearrange them
- In-app browser — multiple agents can now have browsers open simultaneously, each with its own page; background sessions keep their browser state alive so autonomous agents can continue browsing while you work elsewhere
- In-app browser — agents can now drive the browser autonomously to navigate pages, run scripts, and capture screenshots; the panel minimises to a discreet "Agent browsing" indicator you can expand any time to watch the agent live
- Status bar — model and effort are now clickable pills in the status bar (matching the permission-mode picker), replacing the right-sidebar Configuration card; the model badge always shows a short name (e.g. Opus 4.7), so Bedrock ARNs and `default` placeholders never appear in the UI. The model badge now also shows a small provider chip (Anthropic, AWS Bedrock, Google Vertex, or Azure Foundry) so it's clear which backend the session is actually running against. The thinking pill is now interactive too — click to toggle thinking on or off mid-session (mode and budget remain fixed at session start)
- Context and cost details — clicking the Context or Cost rows in the session sidebar now opens dedicated detail modals (segmented context ring with expandable categories, token-mix donut with per-model breakdown), replacing the smaller bottom panels for a clearer, more scannable view
- New session modal — model picker is now a clean **Haiku / Sonnet / Opus** toggle that works for every provider (including Bedrock profiles where models are configured per environment). Permission mode still defaults from your repo's resolved Claude settings, managed-settings allowlists still gate which families you can pick, and the Bypass option is disabled when policy forbids it
- Quick Chat (btw) — opens instantly with no warm-up, and is now explicitly scoped to general questions; for anything that needs to read your code, Otto directs you to a regular session

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
