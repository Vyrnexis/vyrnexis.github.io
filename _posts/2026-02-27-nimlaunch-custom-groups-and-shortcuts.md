---
layout: default
title: "NimLaunch Power Workflows: Custom Groups and Shortcuts"
date: 2026-02-27 04:19:00 +0800
author: "Vyrnexis"
---

NimLaunch gets much more useful once you start treating it like a command hub, not just an app launcher.

Below are practical custom shortcuts and groups I use for Linux ops, dev lookup, quick note creation, clipboard actions, and project jumping.

Add these into `~/.config/nimlaunch/nimlaunch.toml` and adjust paths/commands for your setup.

## 1) Linux Ops Toolbox (`:ops`)

Use one prefix to search logs, check services, or open docs:

```toml
[[groups]]
name = "ops"
query_mode = "pass"

[[shortcuts]]
group = "ops"
label = "journalctl (last 200, grep): "
base = "journalctl -n 200 | rg {query}"
mode = "shell"

[[shortcuts]]
group = "ops"
label = "systemctl status: "
base = "systemctl status {query}"
mode = "shell"

[[shortcuts]]
group = "ops"
label = "Man page search: "
base = "https://man.archlinux.org/search?q={query}"
mode = "url"
```

Examples:

- `:ops pipewire`
- `:ops NetworkManager`

## 2) Dev Lookup Stack (`:dev`)

Search Nim docs, GitHub code, and Arch Wiki from one place:

```toml
[[groups]]
name = "dev"
query_mode = "pass"

[[shortcuts]]
group = "dev"
label = "Nim docs: "
base = "https://nim-lang.org/docs/search.html?q={query}"
mode = "url"

[[shortcuts]]
group = "dev"
label = "GitHub code search: "
base = "https://github.com/search?q={query}&type=code"
mode = "url"

[[shortcuts]]
group = "dev"
label = "Arch Wiki: "
base = "https://wiki.archlinux.org/index.php?search={query}"
mode = "url"
```

Examples:

- `:dev asyncdispatch`
- `:dev systemd user service`

## 3) New Note Command (`:note`)

Create and open a dated Markdown note instantly:

```toml
[[shortcuts]]
prefix = ":note"
label = "New note: "
base = "mkdir -p ~/Notes && nvim ~/Notes/$(date +%F)-{query}.md"
mode = "shell"
run_mode = "spawn"
```

Example:

- `:note nimlaunch-bugs`

## 4) Clipboard Utility Menu (`:clip`)

Handy Wayland clipboard tasks in one menu:

```toml
[[groups]]
name = "clip"
query_mode = "filter"

[[shortcuts]]
group = "clip"
label = "Copy current time"
base = "date '+%Y-%m-%d %H:%M:%S' | wl-copy"
mode = "shell"
run_mode = "spawn"

[[shortcuts]]
group = "clip"
label = "Screenshot area -> clipboard"
base = "grim -g \"$(slurp)\" - | wl-copy"
mode = "shell"
run_mode = "spawn"

[[shortcuts]]
group = "clip"
label = "Clear clipboard"
base = "printf '' | wl-copy"
mode = "shell"
run_mode = "spawn"
```

Notes:

- Requires `wl-copy` (from `wl-clipboard`).
- Screenshot action uses `grim` + `slurp`.

## 5) Project Jump Menu (`:proj`)

Quickly open your main working directories:

```toml
[[groups]]
name = "proj"
query_mode = "filter"

[[shortcuts]]
group = "proj"
label = "NimLaunch repo"
base = "~/Projects/GitHub/Vyrnexis/NimLaunch"
mode = "file"

[[shortcuts]]
group = "proj"
label = "Blog repo"
base = "~/Projects/GitHub/Vyrnexis/vyrnexis.github.io"
mode = "file"
```

## Why This Pattern Works

Instead of memorizing one-off shell aliases, you get discoverable actions under a small set of prefixes:

- `:ops` for system tasks
- `:dev` for research
- `:note` for capture
- `:clip` for utility actions
- `:proj` for navigation

Small configuration changes, big workflow speed-up.
