---
layout: default
title: "Niri-install: Bootstrap a Full Niri Desktop on Arch"
date: 2025-12-06 12:41:00 +0800
author: "Vyrnexis"
---

If you start from a minimal Arch install, building a full Wayland desktop stack by hand can take a while.  
`Niri-install` is my automation script for that exact scenario.

Project:

- [github.com/Vyrnexis/Niri-install](https://github.com/Vyrnexis/Niri-install)

## What This Project Does

`niri_install.sh` turns a fresh minimal Arch setup into a usable Niri desktop with:

- Niri compositor + Waybar
- greetd + tuigreet login flow
- PipeWire audio stack
- Themed GTK/Qt environment variables
- Productivity tooling (Kitty, Thunar, screenshot tools, notifications)
- AUR helper setup and selected AUR apps
- Shell config deployment (`.bashrc` + `.zshrc`) with backup behavior

The script is aimed at repeatable setup, not one-off command copy/paste.

## Why I Built It

I wanted a one-command bootstrap that handles:

- package groups from tracked lists
- service enablement
- user group adjustments
- config sync into `~/.config`
- consistent post-install state after reboot

Instead of rebuilding the same system manually each reinstall, this script turns it into a reproducible workflow.

## Usage

```bash
cd ~
git clone https://github.com/Vyrnexis/Niri-install.git
cd Niri-install
./niri_install.sh
```

Important:

- Run as your normal sudo-capable user (not root).
- Make sure network is working first.
- Reboot after completion so greetd/session services come up cleanly.

## Practical Details Worth Noting

- It uses package set files (`packages/*.txt`) for grouped installs.
- It installs `paru` if missing, then applies AUR package lists.
- Existing shell rc files are timestamp-backed up before replacement.
- It can detect virtualization type and add matching guest tooling.
- It installs NimLaunch and Nymph binaries from their repos as part of the desktop stack.

## Good Fit

This project is best for users who:

- already use Arch
- want Niri on top of a minimal base
- prefer a scripted, repeatable desktop bootstrap over manual assembly

If you like a deterministic setup process, this is exactly that.
