---
layout: default
title: "NimLaunch: A Keyboard-First Launcher for Linux"
date: 2026-02-27 04:18:00 +0800
author: "Vyrnexis"
---

If you live on the keyboard, launching apps should feel instant.  
That is the core idea behind **NimLaunch**: a fast Linux launcher written in Nim, built around fuzzy search, command prefixes, and practical workflow shortcuts.

Unlike many launchers that lean on older X11 stacks, NimLaunch uses **SDL2** for native **Wayland/X11** support with GPU-backed compositing.

## What Makes NimLaunch Useful

- Fuzzy app search with typo tolerance.
- MRU-biased results when the query is empty.
- Prefix-driven actions for themes, shell commands, config files, and file search.
- Optional Vim-style navigation for people who want `j/k`, `gg/G`, and command-bar control.
- Theme support with live preview and persistence.
- Desktop-file icon loading (PNG/SVG), with optional fallback mappings.

## Prefix Commands I Use Most

- `:t` for theme browsing and live preview.
- `:s` for searching files.
- `:c` for jumping into config files under `~/.config`.
- `:r` (or `!`) to run terminal commands quickly.
- `:<group>` shortcuts (default power alias is `:p`).

This prefix model is where NimLaunch really clicks: launcher + command palette + quick action hub in one flow.

## Build And Run

Prebuilt binaries are available on the releases page:

- [NimLaunch Releases](https://github.com/Vyrnexis/NimLaunch/releases)

Or build from source:

```bash
git clone https://github.com/Vyrnexis/NimLaunch.git
cd NimLaunch
nimble -y nimRelease
./bin/nimlaunch
```

Config is created on first run at:

`~/.config/nimlaunch/nimlaunch.toml`

## Quick Config Example

```toml
[window]
width = 500
opacity = 1.0
max_visible_items = 10
center = true
vertical_align = "one-third"

[input]
prompt = "> "
cursor = "_"
vim_mode = false

[terminal]
program = "kitty"
```

## Why I Built It This Way

I wanted a launcher that stays responsive, respects keyboard-first habits, and does more than just open apps. NimLaunch is designed to bridge app launching, shell actions, and custom shortcuts without turning into a heavy desktop dependency.

If you want to try it or dig into the source:

- [github.com/Vyrnexis/NimLaunch](https://github.com/Vyrnexis/NimLaunch)
