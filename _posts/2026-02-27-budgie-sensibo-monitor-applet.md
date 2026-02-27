---
layout: default
title: "Budgie-Sensibo: Control AC Status From the Panel"
date: 2025-12-05 01:56:00 +0800
author: "Vyrnexis"
---

`Budgie-Sensibo` is a simple Budgie applet that shows live Sensibo data and lets you toggle AC power without opening a separate app.

Project:

- [github.com/Vyrnexis/Budgie-Sensibo](https://github.com/Vyrnexis/Budgie-Sensibo)

## What It Does

The applet gives you quick access to:

- current room temperature
- current humidity
- AC on/off state
- one-click power toggle from the panel popover

It is designed for fast status checks in normal desktop use.

## How It Works

Under the hood, the applet:

- talks to the Sensibo API using your API key
- polls measurements at a configurable refresh interval
- updates both text stats and icon state
- exposes settings in Budgie for API key, device ID, and interval

That means you can keep everything in-panel instead of opening the phone app every time you want a quick check.

## Install

Use the included installer script:

```bash
./install.sh
```

Or install manually:

```bash
mkdir build && cd build
meson --buildtype plain --prefix=/usr --libdir=/usr/lib
sudo ninja install
```

Uninstall:

```bash
sudo ninja uninstall
```

## Setup In Budgie

After installing:

1. Add the applet to your Budgie panel.
2. Open applet settings.
3. Enter your Sensibo API key.
4. Enter your Sensibo device ID.
5. Set a refresh interval that suits your usage.

Once configured, the applet starts showing live values and keeps the icon in sync with AC power state.

## Good Fit For

- Budgie users with Sensibo devices
- people who want simple climate status in the panel
- users who prefer lightweight desktop-integrated controls

This project is intentionally small and practical: quick glance, quick toggle, done.
