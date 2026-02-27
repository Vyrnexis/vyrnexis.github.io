---
layout: default
title: "Niri-install: Post-Install Customization Guide"
date: 2025-12-06 12:42:00 +0800
author: "Vyrnexis"
---

After running `niri_install.sh`, the system is usable immediately.  
This guide is for the next step: making the setup truly yours.

Project:

- [github.com/Vyrnexis/Niri-install](https://github.com/Vyrnexis/Niri-install)

## 1) Know What The Script Changed

Primary user-level config target:

- `~/.config/` (synced from the repo)

Shell files:

- `~/.bashrc`
- `~/.zshrc`

These are replaced from repo copies, with timestamped backups created first. If you had personal shell customizations, merge them back from backups.

## 2) Adjust Package Selection At The Source

Niri-install uses package list files so changes are easy to track:

- `packages/pacman-core.txt`
- `packages/pacman-desktop.txt`
- `packages/pacman-audio.txt`
- `packages/pacman-fonts.txt`
- `packages/pacman-extras.txt`
- `packages/paru-apps.txt`
- `packages/paru-themes.txt`

If you fork the repo, this is the cleanest place to tailor what gets installed.

## 3) Tune Niri + Waybar

For day-to-day UI/UX adjustments, start here:

- Niri config under `~/.config/niri/`
- Waybar config under `~/.config/waybar/`

Typical edits:

- keybindings
- workspace behavior
- bar modules/order
- clock/network/audio formatting

The script already sets practical bindings (launcher/terminal/browser/file manager), so this stage is refinement rather than rebuild.

## 4) Theme + Cursor + Environment

The installer writes environment values in:

- `~/.config/environment.d/10-dracula.conf`

This controls variables like:

- `GTK_THEME`
- `XCURSOR_THEME`
- Wayland-related app behavior (`MOZ_ENABLE_WAYLAND`, `QT_QPA_PLATFORM`, etc.)

If you swap themes/cursors later, update this file and re-login.

## 5) Services To Verify

System services:

- `NetworkManager`
- `bluetooth`
- `seatd`
- `greetd`

User services:

- `pipewire.service`
- `pipewire-pulse.service`
- `wireplumber.service`

Quick checks:

```bash
systemctl status greetd
systemctl --user status pipewire wireplumber
```

## 6) Session/Login Tweaks

greetd config path:

- `/etc/greetd/config.toml`

Default command runs Niri via:

`dbus-run-session niri`

If you want alternate startup commands, this is where to edit them.

## 7) Keep Your Fork Maintainable

A simple pattern that works well:

1. Keep package list changes in `packages/*.txt`.
2. Keep desktop config changes in the repo’s `.config/`.
3. Re-run the installer after major edits to verify reproducibility.
4. Commit in small chunks so regressions are easy to isolate.

## 8) Recommended First Custom Pass

If you just finished install, do these first:

1. Merge personal aliases/functions back into shell rc files.
2. Adjust Niri keybindings to your muscle memory.
3. Trim Waybar modules you do not use.
4. Confirm cursor/theme consistency across GTK + Qt apps.
5. Reboot once after major service/theme changes.

The goal is not just a pretty desktop; it is a setup you can rebuild quickly and trust.
