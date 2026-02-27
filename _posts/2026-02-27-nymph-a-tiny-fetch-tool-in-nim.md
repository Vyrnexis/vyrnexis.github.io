---
layout: default
title: "Nymph: A Tiny Fetch Tool Written in Nim"
date: 2025-12-05 20:35:00 +0800
author: "Vyrnexis"
---

I built **Nymph** as a lightweight system fetch utility in Nim: fast startup, simple output, and minimal setup overhead.

Project:

- [github.com/Vyrnexis/Nymph](https://github.com/Vyrnexis/Nymph)

## Why Nymph

I wanted a fetch tool that keeps the output clean but still gives useful flexibility:

- PNG logo rendering for terminals that support Kitty graphics protocol
- Built-in ASCII fallback when graphics support is not available
- Config that stays readable (`key=value`)
- Easy overrides from CLI flags and environment variables

In short: tiny binary, predictable behavior, and no heavy framework.

## Core Features

- Auto logo selection based on distro (`/etc/os-release`)
- `NYMPH_LOGO` and `NYMPH_LOGO_DIR` overrides
- `--logo` support for named logos or absolute image paths
- Configurable max logo width and stats offset
- Optional no-color output mode

Nymph creates `~/.config/nymph/config.conf` on first run, so you can tweak behavior quickly without digging into source.

## Build And Run

```bash
git clone https://github.com/Vyrnexis/Nymph.git
cd Nymph
nimble release
./nymph
```

Alternative build:

```bash
nim c -r src/nymph.nim
```

## Useful Runtime Flags

```bash
nymph --logo arch
nymph --logo /full/path/to/logo.png
nymph --no-color
```

Env-based control:

```bash
export NYMPH_LOGO=arch
export NYMPH_LOGO_DIR="$HOME/.config/nymph/logos"
```

## Example Config

`~/.config/nymph/config.conf`

```conf
maxwidth=200
statsoffset=22
nocolor=false
customlogo=
```

## Logo Search Order

Nymph checks several locations for `<name>.png` logos, including:

- shipped/source `logos/`
- `~/.config/nymph/logos`
- `$NYMPH_LOGO_DIR`
- install-adjacent `logos` paths

If no compatible PNG path is found (or Kitty graphics is unavailable), it falls back to built-in ASCII art so output still works everywhere.

## Good Fit For

- Minimal Linux setups
- Fast shell startup usage
- People who want fetch output that is customizable but not over-engineered

Nymph is intentionally small and focused, and that is exactly the point.
