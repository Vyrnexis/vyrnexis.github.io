---
layout: default
title: "Adobe Portable Installer for Linux: Step-by-Step Walkthrough"
date: 2026-01-22 16:14:00 +0800
author: "Vyrnexis"
---

This is a practical walkthrough for setting up Photoshop/Lightroom portable apps with my installer script on Linux.

Project:

- [Adobe-Portable-Installer-for-Linux](https://github.com/Vyrnexis/Adobe-Portable-Installer-for-Linux)

## 1) Install Dependencies

### Arch Linux

```bash
sudo pacman -S --needed wine winetricks cabextract p7zip file gawk tar desktop-file-utils
```

### Ubuntu

```bash
sudo apt install wine winetricks cabextract p7zip-full file gawk tar desktop-file-utils
```

### openSUSE

```bash
sudo zypper install wine winetricks cabextract p7zip file gawk tar desktop-file-utils
```

## 2) Download The Project

```bash
git clone https://github.com/Vyrnexis/Adobe-Portable-Installer-for-Linux.git
cd Adobe-Portable-Installer-for-Linux
```

## 3) Put Portable Archives Next To Installer

Place these files in the same folder as `Installer.sh`:

- `PhotoshopPortable.tar.gz`
- `LightroomPortable.tar.gz`

You can install one or both; whichever archive is present and selected in the menu gets installed.

## 4) Run The Installer

```bash
chmod +x Installer.sh
./Installer.sh
```

You will be asked:

1. Prefix path: default `~/.adobe` or custom path.
2. What to install:
   - Photoshop
   - Lightroom
   - Both
   - Prefix-only (deps + optional dark mode)
3. Whether to apply Wine dark-mode colors.

## 5) What The Script Does

Under the hood it:

- Initializes a 64-bit Wine prefix.
- Installs winetricks runtime/font/XML dependencies once (marker file in prefix).
- Applies selected overrides.
- Extracts selected app archive(s) into:
  - `PREFIX/drive_c/PortableApps/Photoshop`
  - `PREFIX/drive_c/PortableApps/Lightroom`
- Generates desktop entries in `~/.local/share/applications`.

## 6) Verify Installation

Check these:

```bash
ls ~/.local/share/applications/photoshop.desktop
ls ~/.local/share/applications/lightroom.desktop
```

If you used a custom prefix, verify files exist there:

```bash
ls /your/custom/prefix/drive_c/PortableApps
```

## 7) Troubleshooting

Installer logs are written to:

`PREFIX/logs`

Useful files:

- `wineboot.log`
- `winetricks-deps.log`
- `msvcp140-repair.log`
- `photoshop-extract.log`
- `lightroom-extract.log`

If setup fails, check logs first before rerunning.

## 8) Uninstall Cleanly

```bash
chmod +x Uninstaller.sh
./Uninstaller.sh
```

Or use flags:

```bash
./Uninstaller.sh --photoshop
./Uninstaller.sh --lightroom
./Uninstaller.sh --all
```

Important: use the same custom prefix path during uninstall that you used during install.

## Optional: Add Your Own Screenshots

If you want this post to be more visual, add screenshots to `assets/` and insert them like:

```markdown
![Installer menu]({{ '/assets/your-installer-screenshot.png' | relative_url }})
```

That is the full flow from clean machine to launchers on your desktop.
