# Changelog

All notable changes to Otto will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added

- Command Centre — three alternative session views (Neural Pulse, Mission Timeline, Cockpit HUD) with floating action bar and shared modal orchestration

### Improved

- Neural Pulse activity graph — concentric temporal rings replace spiral layout, tiered rendering supports 300+ tool calls, sub-agent connectivity with mini-bubble orbits, and smooth layout transitions
- In-app browser — now embedded directly in the session panel with a resizable viewport and toolbar, replacing the separate browser window
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
