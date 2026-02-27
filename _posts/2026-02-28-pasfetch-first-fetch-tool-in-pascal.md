---
layout: default
title: "Pasfetch: My First Fetch Utility (Pascal)"
date: 2025-12-05 01:48:00 +0800
author: "Vyrnexis"
---

Before Nymph, there was `Pasfetch` - my first fetch utility, written in Pascal.

Project:

- [github.com/Vyrnexis/Pasfetch](https://github.com/Vyrnexis/Pasfetch)

## Why It Matters

`Pasfetch` was the early foundation for how I like fetch tools:

- lightweight output
- distro-specific logo styling
- practical system info at a glance

It started as a work-in-progress project, but it established the direction I later refined in Nim.

## What It Shows

Pasfetch gathers core host details such as:

- OS
- hostname
- kernel
- shell
- package count
- uptime
- memory usage

It then renders the matching ASCII logo and system info together in a clean terminal view.

## Implementation Layout

The code is split into small Pascal units:

- `pasfetch.pas` as entry point
- `uPasfetchUtils.pas` for system info helpers
- `uPasfetchAscii.pas` for logo + display logic
- `uAnsiCrt.pas` for ANSI terminal handling

That modular layout made it easier to expand logos and tweak display behavior.

## Build And Run

Install Free Pascal Compiler (`fpc`) and a Nerd Font for icon rendering, then compile:

```bash
fpc -Px86_64 -CpCOREAVX2 -CfAVX2 -OpCOREAVX2 -O3 -Mobjfpc -CX -B -XXs -v pasfetch.pas
```

Or use the included script:

```bash
./build.sh
```

Run:

```bash
./pasfetch
```

## Good Fit For

- Pascal users who want a terminal utility project to study
- people interested in the evolution from Pasfetch to Nymph
- anyone who likes small, direct CLI tools

Pasfetch is where the fetch-tool journey started for me.
