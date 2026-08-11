# Changelog

All notable changes to Otto will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added

- Five brand themes, each in dark and light, switchable from a picker in the header — your choice persists across reloads
- Attach files to a prompt — drag files onto the composer, paste them, or use the paperclip picker; any file type is supported, not just images. Files are referenced by their real location so Claude reads them in place with no copying, and can grep or re-read them if they change
- Plugin contents — browse cards, marketplace rows, and detail pages now show what a plugin ships: icon-pill counts for skills, agents, commands, hooks, MCP servers, and LSP servers, with a full named breakdown and descriptions on the detail page. Works even for marketplace plugins you haven't installed yet
- Fable model tier — Fable is now selectable alongside Opus, Sonnet, and Haiku: configure it per provider in the Model Configuration card and pick it in the new-session model selector
- Auto-dream — the Memory tab's Auto-dream toggle now actually works: a **Dream now** button opens a pre-filled session to consolidate learned memories on demand, and the toggle schedules nightly consolidation that runs reliably on every supported provider
- Branch changes panel — the "Files changed" tile now shows a live diffstat of your branch against main (instead of just the agent's own edits), and clicking it opens a slide-over with branch and push state, your linked pull request (review and CI status), the branch's own commits, and every changed file grouped as Staged / Unstaged / Untracked, each opening its diff. Available from every session view
- Branch changes panel — the branch's own commits now expand in place to show the files they touched, with change counts; click a file to open its diff at that commit
- Default session view — a browser card now sits at the top of the receipts row whenever an agent has a page open, showing the page title, status, and a live preview of its most recent capture, with arrows to look back through recent screenshots
- Stage overview — Working and Needs Attention cards now show a thumbnail of the agent's most recent browser capture alongside the card text, so you can spot who's driving a page at a glance
- Default session view (the Handover) — a new session view, now the default, built around the moment you return to a session: top to bottom it shows why you're here, what happened, and what's being asked. A state banner surfaces the session's phase at a glance (needs your decision, working, turn finished, or failed); permission and question prompts render inline as the page's primary element instead of popping up as separate dialogs; the agent's latest message sits front and centre with controls to cycle back through earlier updates; and a receipts row shows outcome-shaped evidence — files changed with diffstats you can click through to, command pass/fail counts, and task progress. Dashboard, Neural Pulse, Timeline, and Cockpit remain available from the view picker
- Tasks panel — the Tasks tile in the receipts row now opens a slide-over like Files and Commands, showing each task's description, dependencies resolved to their subjects rather than raw ids, owner, and live status history, instead of expanding in place and pushing the rest of the row out of view
- Session lineage — the Stage and Default view now show which session spawned which. Stage cards get a subtle marker naming the related session, and hovering it highlights the other side of the pairing wherever it sits; the Default view's Crew lane pins delegated sessions ahead of sub-agents, with the parent named above
- Default session view — plan review now happens inline instead of opening a separate dialog: the plan sits alongside the approval controls, and highlighting any passage pins a note right beside it, so feedback stays attached to the line it's about instead of collecting in a separate list
- Default session view — the same highlight-to-feedback now works on the agent's latest message: pin a note to a passage and it rides along with your next reply. Paging back through earlier updates keeps the right notes on the right update, and stepping back no longer snaps back to the newest one the moment the agent says something else

### Improved

- Neural Pulse — reworked into a token-sized orbit constellation: each prompt anchors a hub with its thinking and tool calls orbiting it, orb size now scales with token usage (sub-agent orbs grow live as they work), and the layout stays stable as the session grows, with lit-sphere orbs, spawn animations, and a nebula backdrop
- Transcript clarity — responses cut short by an interrupt now carry an **(interrupted)** marker so you know they may be incomplete; turns fired by a scheduled task are tagged **(scheduled)** at session end; Bash commands that hit their timeout and were moved to the background show an "auto-backgrounded" note; and a sub-agent waiting out a rate limit now shows a "retrying" line instead of looking hung
- Auto-mode transparency — when a session in auto permission mode automatically denies a tool request, the transcript now records an **Auto-denied** entry with the reason, so blocked actions are visible instead of failing silently
- Automations effort control — cron and webhook automations can now set a reasoning effort level (Low, Medium, High, Extra High, Max) from the Configuration panel, matching the in-session effort picker; unset leaves it at the default
- Default session view — the layout is now a fixed frame that fills the window instead of a scrolling page: reports no longer sit inside a scrollbar within a scrollbar, and the view makes better use of wide screens
- Agent orchestration — a session now keeps track of every related session it's connected to (who spawned it, and what it's spawned), so agents can find and message each other reliably across multi-step chains, and this survives the conversation being compacted
- Default session view — running sub-agents now show as live strips (what they're doing, tool activity, tokens, elapsed time) that sit above the prompt, and finished sub-agents collapse to a compact roll call; click either to open the full sub-agent conversation
- Composer and status bar — the prompt box and status row read as one calmer surface: pinned commands moved into the composer's own footer next to Send, Stop/Resume moved up onto the status row so it ends in an action rather than trailing off, and mode/model/effort controls now show as plain text that only gains colour and a surface on hover — so colour is reserved for things that need attention
- Visual previews — options and their preview now sit side by side instead of stacked, so you can compare choices and the mockup without scrolling. Previews render at their natural height instead of being cropped, and light-background designs now show up with readable dark text instead of being forced into unreadable light text

### Fixed

- Default view no longer shows "Over to you" while an agent is still working — this could happen when a session was started by an automation or cron (it looked idle from the moment it started) or when the main turn finished but a sub-agent was still running (now shown as "N sub-agent(s) working" instead)
- Question options with a comma in their label (e.g. "Centred card, heavy scrim") could get scrambled and fail to select or submit correctly — fixed
- Context gauge is back — the sidebar row, Cockpit HUD, and other in-session indicators show live context usage again, ticking up as you work, and no longer flicker between different values while sub-agents are running. Context and cost now survive a page reload without dropping, and the context detail modal's headline figures match what the sidebar shows instead of disagreeing with it. On Bedrock the old approach risked triggering extra billed background calls; the gauge is now driven by usage figures Otto already receives, so showing it costs nothing extra
- Tool summaries in the Working banner and status bar no longer cut off mid-string while the box still has room — long commands and file paths now fill the available space and clip cleanly at the true edge instead of ending early with an ellipsis
- New files created by an agent now show their diff correctly in the branch changes panel — previously they showed "No diff data available"
- Task tracking — task descriptions, blockers, and ownership now actually reach the dashboard; previously this data silently failed to arrive, so tasks only ever showed a bare title and status
- Panels no longer get stuck on "Loading…" when opened right as Otto connects or reconnects — Hooks, Memory, Plugins, and a session's history now recover on their own instead of requiring a page reload
- Agent orchestration — messages one agent sends to another are now clearly marked as coming from that agent instead of looking like they came from you, and the sender's name displays correctly (some sessions previously showed up labelled as "titled"). Spawning a session no longer risks the caller getting stuck waiting for a reply that may never come

## [0.6.0] - 2026-07-08

### Added

- Live token visibility — sessions now show token usage alongside cost everywhere it matters: a dual cost/tokens gauge with a LIVE indicator in the Cockpit HUD, a combined cost·tokens row on the session panel and list cards, and a total-tokens headline with cache hit rate and exact counts in the cost detail view. The token count ticks up as the agent works
- Memory tab — top-level home for Claude memory, unifying Instructions (CLAUDE.md hierarchy across user and project levels) and Learned (auto-memory) entries; view, edit, create, and delete at any level you own, with behaviour settings tucked into a collapsible section
- Stage — tiered session overview (Needs Attention, Working, Idle, Inactive) replacing the fleet inbox for clearer prioritisation at a glance
- PR merge conflicts surfaced — conflicted pull requests in the GitHub panel are flagged with a red merge icon, and a one-click **Resolve conflicts** action launches a worktree agent that merges the base branch in, runs your checks, and pushes the fix without ever force-pushing
- Auto-approval — sessions in "auto" permission mode automatically approve safe tool requests; uncertain or risky requests still prompt for manual approval
- Automations tab — top-level home for cron and webhook automations, with structured form editors, live event feed, and Insights showing top event types, recent volume patterns, and one-click suggestions for frequent events
- Automations safety — crons and webhooks are now off by default with per-repo on/off toggles in the header, so each repo opts in independently and nothing runs until you do (state resets on restart)
- Hooks tab — top-level home for hook management, with structured editors, a test panel for dry-run and live execution against synthesised payloads, recent-fires strip showing real execution outcomes per hook, enable/disable without deletion, and inline rename
- Agent orchestration — sessions can now spawn child sessions and send messages to one another, enabling one agent to delegate work, coordinate with peers, and wait for results before continuing
- Plan approval redesign — approve a plan with a single action that bundles the implementation permission mode (Ask / Accept edits / Auto / Bypass), a reasoning effort selector (defaulting to the level carried over from planning), an optional model switch, and a Fresh context toggle, so you can plan with one model and build with another (e.g. plan with Opus, implement with Sonnet on a clean context). The standalone "Clear context" sidebar action remains available for wiping a session mid-flight.
- Background sub-agents — a **Background** button on each running sub-agent row (and in the sub-agent detail modal) lets a long-running sub-task continue on its own so the parent turn doesn't have to wait; the Sub-agents section header now shows a live count of how many tasks are running in the background

### Fixed

- Environment isolation — Otto no longer leaks a `PORT` variable into agent sessions, which previously caused user tools (Express, Next.js, test harnesses) to bind to the wrong port
- Worktrees with uncommitted changes or unpushed commits are no longer deleted when a session stops — only clean worktrees are auto-cleaned
- Cost tracking — the Stage header's "today" figure and per-repo totals are now sourced from the provider's reported cost rather than estimated from token counts, so Bedrock, Vertex, and Azure users see accurate numbers instead of a Sonnet-priced approximation
- Provider auth — forking a session or resuming a session after restart no longer drops the active provider profile, so Bedrock, Vertex, and Azure users stay signed in instead of being prompted to log in again
- Inactive sessions no longer lose their cost badge when you open them — previously the recorded cost was visible in the list but vanished as soon as the session was opened
- Session cost no longer disappears — spend now survives reconnecting, reloading the page, restarting the app, and clearing a session's context, so the figure you see always reflects what you've actually spent
- In-app browser — agent-triggered browser sessions now consistently open inline in the dashboard panel; previously a timing race could cause a separate browser window to appear instead
- Slash commands and skills are now available after resuming an idle session — previously the plugin list was not refreshed on resume, so skills disappeared until the session was restarted
- Model switching — the status-bar picker no longer shows a duplicate "Custom model" row alongside the resolved tier; switching model mid-session no longer leaves the session stuck on "Working"; and a failed model change now surfaces an inline error chip instead of silently doing nothing
- Effort picker — the in-session status-bar picker no longer hides "Extra High" mid-session; all five effort levels (Low, Medium, High, Extra High, Max) are now consistently available in both the new-session modal and the in-session picker
- GitHub tab no longer stalls on "Loading…" on first load or after a reconnect — counts now populate as soon as GitHub responds, and reconnecting repopulates the tab from cache instantly
- GitHub panel — the packaged desktop app no longer reports `Executable not found in $PATH: "gh"` when GitHub CLI is installed via Homebrew or another non-default location; bundled tool lookups now find Homebrew, MacPorts, and `~/.local/bin` installations automatically
- Stale "running" sub-agent rows are now cleaned up automatically — Otto reconciles against the agent runtime's view of active sub-agents on reconnect and at turn end, so ghost rows from dropped messages or replay gaps disappear on their own

### Improved

- Session auto-naming — unnamed sessions are automatically titled from the plan heading when a plan is approved
- Navigation — streamlined icon rail layout with direct routing to Stage, Worktrees, GitHub, Plugins, and Config
- Sub-agent modal — live metadata updates, conversation auto-scroll with sticky scroll-to-bottom, and full response display without truncation
- Auto-updater — pre-release channel support with tray toggle; RC versions automatically receive pre-release updates
- Worktrees — gitignored files listed in `.worktreeinclude` (e.g. `.env`) are now automatically copied into Otto-created worktrees
- Permissions settings — unified rule-centric view across user, project, and local scopes, with conflict detection (duplicates, allow/deny clashes, wildcard shadowing), a guided Add Rule wizard, scope-chip move/duplicate, and bulk select with drag-and-drop
- Plugins — unified browse view across all configured marketplaces (no per-marketplace dropdown), dedicated detail pages with author, repository, licence, and keywords, inline scope management, and visual polish matching the Stage page
- Automations editing — cron and webhook rules now have structured editors with live schedule previews and match-builder chips; the Form/Raw toggle keeps the underlying file accessible for power users
- Stage cards — per-session cost is now shown directly on every card (Needs Attention, Working, Inactive), so you can see spend per session at a glance without opening it
- Project tabs — drag to reorder projects in the header; the order is remembered across reloads, and each project's dot colour stays stable when you rearrange them
- In-app browser — multiple agents can now have browsers open simultaneously, each with its own page; background sessions keep their browser state alive so autonomous agents can continue browsing while you work elsewhere
- In-app browser — agents can now drive the browser autonomously to navigate pages, run scripts, and capture screenshots; the panel minimises to a discreet "Agent browsing" indicator you can expand any time to watch the agent live
- In-app browser — the modal now shows a slim activity row at the top so you can still see what the agent is doing (thinking, writing, tool use, or idle) while a page is on screen
- Status bar — model and effort are now clickable pills in the status bar (matching the permission-mode picker), replacing the right-sidebar Configuration card; the model badge always shows a short name (e.g. Opus 4.7), so Bedrock ARNs and `default` placeholders never appear in the UI. The model badge now also shows a small provider chip (Anthropic, AWS Bedrock, Google Vertex, or Azure Foundry) so it's clear which backend the session is actually running against. The thinking pill is now interactive too — click to toggle thinking on or off mid-session (mode and budget remain fixed at session start)
- Context and cost details — clicking the Context or Cost rows in the session sidebar now opens dedicated detail modals (segmented context ring with expandable categories, token-mix donut with per-model breakdown), replacing the smaller bottom panels for a clearer, more scannable view
- New session modal — model picker is now a clean **Haiku / Sonnet / Opus** toggle that works for every provider (including Bedrock profiles where models are configured per environment). Permission mode still defaults from your repo's resolved Claude settings, managed-settings allowlists still gate which families you can pick, and the Bypass option is disabled when policy forbids it

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
