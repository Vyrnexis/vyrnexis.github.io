---
layout: default
title: "Cinnamon-Sensibo: The One I Use Most"
date: 2025-12-05 01:55:00 +0800
author: "Vyrnexis"
---

This is my Cinnamon version of the Sensibo panel tool, and honestly it is the one I use most day-to-day.

Project:

- [github.com/Vyrnexis/Cinnamon-Sensibo](https://github.com/Vyrnexis/Cinnamon-Sensibo)

## What It Does

`Cinnamon-Sensibo` gives you quick control from the Cinnamon panel:

- shows temperature and humidity from Sensibo
- shows current AC on/off state
- provides an on/off toggle directly in the applet menu
- refreshes on a timer you can configure

No separate full app needed for basic climate checks.

## Why A Cinnamon Version

I already had a Budgie implementation, but Cinnamon is where I spend more time, so I wanted the same fast workflow in the panel I actually use the most.

The applet is small and focused:

- JavaScript applet UI (`applet.js`)
- Python helper for Sensibo API calls (`sensibo.py`)
- settings schema for refresh interval + credentials

## Install

Clone the repo and copy the applet folder into your local Cinnamon applets directory:

```bash
git clone https://github.com/Vyrnexis/Cinnamon-Sensibo.git
mkdir -p ~/.local/share/cinnamon/applets
cp -r Cinnamon-Sensibo/sensibo@drunkenalcoholic ~/.local/share/cinnamon/applets/
```

Then restart Cinnamon (or log out/in), open Applets, and enable `sensibo@drunkenalcoholic`.

## Configure

In applet settings, set:

- `API key` from your Sensibo account
- `Pod UUID` for your device
- `Refresh interval` in seconds

Once those are set, the applet starts polling data and the switch controls AC state directly.

## Good Fit For

- Cinnamon desktop users with Sensibo hardware
- users who want quick panel-level control
- anyone who prefers a simple tool over a heavyweight dashboard

This one is built for practical daily use: check stats, toggle power, move on.
