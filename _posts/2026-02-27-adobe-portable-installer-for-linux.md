---
layout: default
title: "Adobe Portable Installer for Linux: One Prefix, Clean Setup"
date: 2026-01-22 16:13:00 +0800
author: "Vyrnexis"
---

I put together **Adobe Portable Installer for Linux** to make Wine-based setup less repetitive and easier to maintain over time.

Project link:

- [github.com/Vyrnexis/Adobe-Portable-Installer-for-Linux](https://github.com/Vyrnexis/Adobe-Portable-Installer-for-Linux)

## What It Solves

Manual Wine setup for portable apps usually turns into a checklist you repeat every reinstall:

- Build a prefix
- Install the same winetricks components
- Extract app files into the right place
- Create desktop launchers
- Clean up properly when uninstalling

This project automates that flow with installer and uninstaller scripts.

## Core Behavior

The installer is built around a **single Wine prefix** (default `~/.adobe`, with custom path support):

- Initializes a 64-bit prefix
- Applies required winetricks dependencies once (marker-based)
- Sets Windows version and DLL overrides
- Extracts Photoshop/Lightroom portable archives into `drive_c/PortableApps/...`
- Generates `.desktop` launchers in `~/.local/share/applications`
- Optionally applies a dark-mode registry color patch

It also writes step logs under `PREFIX/logs`, which makes troubleshooting much easier than a silent fail.

## A Practical Detail I Added

There is a specific Wine/winetricks edge case where `msvcp140.dll` can land in a broken 32-bit state under `system32` for this workflow.  
The installer checks for that and attempts a repair automatically so users do not need to debug DLL internals manually.

## Quick Start (Arch Example)

```bash
sudo pacman -S --needed wine winetricks cabextract p7zip file gawk tar desktop-file-utils
chmod +x Installer.sh
./Installer.sh
```

Then choose:

- Photoshop
- Lightroom
- Both
- Prefix-only setup

## Uninstall Options

Uninstaller supports interactive mode and flags:

```bash
chmod +x Uninstaller.sh
./Uninstaller.sh
```

Or directly:

```bash
./Uninstaller.sh --photoshop
./Uninstaller.sh --lightroom
./Uninstaller.sh --all
```

`--all` removes app artifacts, desktop entries, and the selected prefix.

## Notes

- Use the same prefix path for install and uninstall if you use a custom location.
- Keep your app archives in the same folder as `Installer.sh`.
- Use this with software and assets you are legally entitled to run.

The goal of this project is simple: reproducible setup, cleaner teardown, less time spent fixing repeated Wine boilerplate.
