---
layout: default
title: "BytePatcher: In-Place Binary Patching in Nim"
date: 2025-12-05 01:51:00 +0800
author: "Vyrnexis"
---

`BytePatcher` is a Nim utility for targeted in-place binary patching, with a safety-first flow before anything gets written.

Project:

- [github.com/Vyrnexis/BytePatcher](https://github.com/Vyrnexis/BytePatcher)

## What It Does

The tool scans a target binary for predefined byte signatures, then writes replacement bytes at matched offsets.

Built-in flow:

- search for patch patterns (with wildcard support)
- print matched offsets
- create a timestamped backup
- ask for confirmation before patching
- apply patch bytes in place
- show MD5 before and after

That sequence keeps patching explicit and traceable.

## Why This Exists

Sometimes you want a direct patch tool without heavy frameworks or a full reverse-engineering UI.  
This project keeps it scriptable and focused while still adding guard rails.

## Implementation Notes

The patch set is defined directly in source (`sublimePatch.nim`) as `Patch` objects:

- `pattern`: bytes to locate
- `data`: bytes to write
- `address`: resolved at runtime

The matcher supports wildcard bytes in patterns, making signatures more tolerant across nearby binary variations.

## Build

```bash
git clone https://github.com/Vyrnexis/BytePatcher.git
cd BytePatcher
nimble install checksums
nim c -d:release sublimePatch.nim
```

## Run

```bash
./sublimePatch
```

The current target path is set in code (`FilePath`), so adjust that to your environment before running.

## Good Fit For

- controlled binary patch workflows
- repeatable patch steps with visible checksums
- Nim users who want a compact, readable patch utility

It is a practical tool: find, verify, back up, patch.
