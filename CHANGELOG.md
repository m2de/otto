# Changelog

All notable changes to Otto will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added

- Stage — tiered session overview (Needs Attention, Working, Idle, Inactive) replacing the fleet inbox for clearer prioritisation at a glance
- Git dashboard — interactive branch spine with ahead/behind indicators and dedicated branch detail pages (changes, commits, status)
- Session search — fuzzy search input in the session list, filtering by title, branch, worktree, and initial prompt; composes with status filters

### Improved

- Navigation — streamlined icon rail layout with direct routing to Stage, Repo, Worktrees, GitHub, Plugins, and Config
- Sub-agent modal — live metadata updates, conversation auto-scroll with sticky scroll-to-bottom, and full response display without truncation
- Auto-updater — pre-release channel support with tray toggle; RC versions automatically receive pre-release updates
- Worktrees — gitignored files listed in `.worktreeinclude` (e.g. `.env`) are now automatically copied into Otto-created worktrees

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
