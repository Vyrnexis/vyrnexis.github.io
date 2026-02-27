---
layout: default
title: "Nymph Logo Packs and Terminal Compatibility Tips"
date: 2025-12-05 20:36:00 +0800
author: "Vyrnexis"
---

This is the practical follow-up for Nymph users who want custom branding and predictable output across different terminals.

Main project:

- [github.com/Vyrnexis/Nymph](https://github.com/Vyrnexis/Nymph)

## 1) Understand The Rendering Model

Nymph has two output paths:

- **PNG logo rendering** when Kitty graphics protocol is supported.
- **ASCII fallback** when graphics are unavailable.

That fallback is a feature, not a failure. It keeps output readable in minimal terminals, remote sessions, and constrained environments.

## 2) Create Your Own Logo Pack

The easiest user-managed location is:

`~/.config/nymph/logos`

Create it and add files:

```bash
mkdir -p ~/.config/nymph/logos
cp mylogo.png ~/.config/nymph/logos/vyrnexis.png
cp otherlogo.png ~/.config/nymph/logos/workstation.png
```

Nymph resolves named logos as `<name>.png`, so this works:

```bash
nymph --logo vyrnexis
nymph --logo workstation
```

## 3) Make A Reusable "Logo Pack" Repo

If you manage multiple machines, keep your logos in a git repo:

```bash
git clone https://github.com/you/nymph-logos.git ~/.config/nymph/logos
```

Then every host can share the same names and usage (`--logo laptop`, `--logo desktop`, etc.).

## 4) Set Better Defaults In Config

`~/.config/nymph/config.conf`

```conf
maxwidth=220
statsoffset=24
nocolor=false
customlogo=
```

Notes:

- `maxwidth` keeps large PNGs from wrecking alignment.
- `statsoffset` can be nudged right if your logo style is visually dense.
- `customlogo` is useful for pinning one exact image path.

## 5) Terminal Compatibility Workflow

When tuning a new logo, test in both modes:

```bash
nymph --logo vyrnexis
NYMPH_LOGO=vyrnexis nymph --no-color
```

What to verify:

- PNG mode: logo is sharp and stats are aligned.
- Fallback mode: text output is still clean and spacing is acceptable.

If alignment is off in PNG mode, reduce `maxwidth` before changing anything else.

## 6) Design Tips For Better Logos

- Use transparent PNG backgrounds.
- Avoid extremely wide images; they force large offsets.
- Keep visual weight centered so stat columns feel stable.
- Export at clean dimensions (e.g., 256 px wide source, scaled by `maxwidth`).

## 7) Fast Shell Aliases

```bash
alias nf='nymph'
alias nfw='NYMPH_LOGO=workstation nymph'
alias nfl='NYMPH_LOGO=laptop nymph'
```

This gives quick identity presets per machine without touching config each time.

## Final Take

If you treat logos as a first-class part of your setup, Nymph becomes more than a fetch line; it turns into a lightweight system identity layer that still degrades cleanly when graphics support is not present.
