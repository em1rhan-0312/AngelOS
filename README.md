<div align="center">
  <img src="docs/logo.png" width="240" alt="Angel OS logo"/>
  <h1 align="center">Angel OS</h1>
  <p align="center"><b>Fly With Your Angel</b></p>
  <p align="center">A clean, fast and ready-to-use Linux distribution with a simple installer, a complete office and development toolkit, and its own identity.</p>
  <p align="center">
    <a href="https://em1rhan-0312.github.io/angelos-web/">Website</a> ·
    <a href="https://instagram.com/angel0sofficial">Instagram</a> ·
    <a href="https://gitlab.com/emirhan.0312">GitLab</a> ·
    <a href="https://github.com/em1rhan-0312">GitHub</a> ·
    <a href="https://github.com/em1rhan-0312/angelos-web">Site source</a>
  </p>
</div>

<div align="center">
  <a href="https://buymeacoffee.com/emirhan0312" target="_blank">
    <img src="https://img.shields.io/badge/BUY_ME_A_COFFEE-FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black" alt="Buy Me A Coffee">
  </a>
</div>

## Table of Contents

- [Overview](#overview)
- [Features](#features)
  - [Installer](#installer)
  - [Desktop and Look](#desktop-and-look)
  - [Preinstalled Software](#preinstalled-software)
  - [Angel Welcome](#angel-welcome)
- [Download](#download)
- [System Requirements](#system-requirements)
- [Installation](#installation)
  - [Virtual Machine](#virtual-machine)
- [Kernels](#kernels)
- [Angel OS Repository](#angel-os-repository)
- [Build from Source](#build-from-source)
- [Project Layout](#project-layout)
- [Roadmap](#roadmap)
- [Project-0312](#project-0312)
- [Support & Community](#support--community)
- [Credits](#credits)

## Overview

Angel OS is a rolling-release distribution built to be installed in minutes and used right away. You get a polished desktop, an installer that does not ask technical questions you do not care about, and a software selection that covers work, study and everyday use out of the box.

> [!NOTE]
> Angel OS is in **alpha**. The first public ISO (`2026.10.31`) is out. Expect rough edges, try it in a virtual machine first and do not install it on a disk with important data.

## Features

### Installer

- Simple step-by-step installer with Angel OS branding
- Welcome screen written in 12 languages
- Steps: language, location, keyboard, partitions, users, summary, install
- Extra kernels (`linux-lts`, `linux-zen`, `linux-hardened`) can be picked in the Angel Welcome window before installing
- One desktop, no questions about it
- Online install: the newest packages are downloaded during setup

### Desktop and Look

- KDE Plasma (Wayland) desktop with the Angel OS application launcher
- Plasma Login Manager as the login screen (SDDM is used as a fallback)
- Dolphin, Firefox and System Settings pinned to the taskbar
- Boot splash (Plymouth) with the Angel wings on black
- Four dark wallpapers: **Angel Mesh** (default), Angel Dark, Angel Blue, Angel Crimson
- Terminal greeting with the Angel OS logo (`fastfetch`)
- PipeWire audio and NetworkManager networking

### Preinstalled Software

| Category | Applications |
| :--- | :--- |
| **Office** | LibreOffice (Writer, Calc, Impress, Draw, Base, Math) |
| **Development** | Visual Studio Code (Code - OSS build), Git, Geany, base-devel, Vim, Nano |
| **Internet** | Firefox |
| **Files and Archives** | Dolphin, Ark |
| **Documents and Images** | Okular, Gwenview, Spectacle |
| **Media** | mpv |
| **Windows apps** | Wine, Winetricks (run many `.exe` programs; compatibility varies) |
| **System** | Konsole, KCalc, KDE Partition Manager, Timeshift (backups), htop, fastfetch |

> [!TIP]
> The Visual Studio Code in the repositories is the open-source **Code - OSS** build. Some Microsoft-only extensions are not available in it; the rest of the extension ecosystem works through Open VSX.

### Angel Welcome

The welcome window opens at the first start and gives you quick access to:

- Install Angel OS (live session only)
- Update system
- Install extra kernels
- Settings, terminal, browser
- Community links

Untick *Show this window at startup* to hide it on an installed system. Start it again any time from the application menu.

## Download

| File | SHA256 |
| :--- | :--- |
| [`angel-os-2026.10.31-x86_64.iso`](https://www.mediafire.com/file/y3mh4oc56pvebfc/angel-os-2026.10.31-x86_64.iso/file) | `8359971c8b02313a2f95f925c86a538a1fc0b5e5e043ba89a3c1807984fa9d59` |

The link opens the MediaFire page; press its download button there. Verify your download:

```bash
sha256sum angel-os-2026.10.31-x86_64.iso
```

On Windows (PowerShell): `Get-FileHash angel-os-2026.10.31-x86_64.iso -Algorithm SHA256`

## System Requirements

| | Minimum | Recommended |
| :--- | :--- | :--- |
| CPU | 64-bit (x86_64) | 64-bit, 2+ cores |
| RAM | 2 GB | 4 GB |
| Disk | 15 GB | 30 GB |
| Network | Required for installation | Wired or Wi-Fi |

## Installation

1. Write the ISO to a USB drive (Ventoy, balenaEtcher, or `dd`) and boot from it.
2. The live desktop starts automatically. Open **Install Angel OS** from the welcome window or the desktop.
3. Follow the installer: language, location, keyboard, partitions, users, summary.
4. Wait for the system to download and install, then reboot.

### Virtual Machine

Recommended VirtualBox settings:

- 4 GB RAM, 2 or more CPU cores
- Enable **EFI** under System
- Display: **VMSVGA**, 128 MB video memory, 3D acceleration **off**
- 30 GB or more of virtual disk for a full install

## Kernels

The standard `linux` kernel is installed by default. Pick extra kernels in the Angel Welcome window before installing, or add them later:

| Package | Best for |
| :--- | :--- |
| `linux` | General use (default) |
| `linux-lts` | Stability, long-term support |
| `linux-zen` | Desktop responsiveness and gaming |
| `linux-hardened` | Security hardening |

```bash
sudo pacman -S linux-lts linux-lts-headers
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

Pick the kernel from the boot menu (Advanced options).

## Angel OS Repository

Angel OS' own packages (such as `angel-welcome`) are built from the PKGBUILDs in [`repo/`](repo/README.md). To host your own copy, see that folder's README. A GitLab CI pipeline ([`.gitlab-ci.yml`](.gitlab-ci.yml)) publishes the repository through GitLab Pages.

## Build from Source

On Arch Linux with `archiso` installed:

```bash
git clone https://github.com/em1rhan-0312/AngelOS.git
cd AngelOS
sudo ./build.sh        # the ISO is written to out/
./test-vm.sh out/angel-os-*.iso   # optional: try it in QEMU
```

The build needs several GB of free disk space and an internet connection.

## Project Layout

| Path | What it is |
| :--- | :--- |
| `build.sh` | Builds the ISO on top of the official archiso `releng` profile |
| `overlay/` | Angel OS changes: package list, branding, boot files, live user |
| `overlay/airootfs/etc/calamares/` | Calamares installer config, branding and install scripts |
| `overlay/airootfs/usr/local/bin/` | `angel-welcome`, `angel-installer`, `angel-set-wallpaper` |
| `repo/` | PKGBUILDs and tooling for the `[angel]` pacman repository |
| `docs/` | Logo and banner images |

## Roadmap

- [x] archiso profile with KDE Plasma desktop
- [x] Angel OS name, boot splash, logo and four wallpapers
- [x] Calamares online installer
- [x] Angel Welcome app and kernel choice
- [x] Plasma Login Manager and NetworkManager out of the box
- [x] First public ISO (`2026.10.31` alpha)
- [ ] Polish the installer slideshow
- [ ] Publish the `[angel]` pacman repository
- [ ] Automated builds and version numbers
- [ ] Stable release after alpha

## Project-0312

Angel OS is developed under the **Project-0312** umbrella.

## Support & Community

- **Instagram (official):** [@angel0sofficial](https://instagram.com/angel0sofficial)
- **Developer:** [@me1nmacht](https://instagram.com/me1nmacht) · [GitLab](https://gitlab.com/emirhan.0312) · [GitHub](https://github.com/em1rhan-0312)
- **Email:** jinglelot@gmail.com

Bug reports and ideas are welcome as issues on GitHub or GitLab.

## Credits

Angel OS is an independent project, built on the work of many others:

- **[Arch Linux](https://archlinux.org)** and **[archiso](https://gitlab.archlinux.org/archlinux/archiso)**: foundation distribution and ISO tooling
- **[KDE](https://kde.org)**: Plasma desktop and applications
- **[Calamares](https://calamares.io)**: installer framework (GPL-3.0-or-later)
- **[LibreOffice](https://www.libreoffice.org)**, **[Code - OSS](https://github.com/microsoft/vscode)**, **[Firefox](https://www.mozilla.org/firefox/)** and the many other open-source projects shipped on the ISO
- **[plymouth-theme-arch10](https://github.com/eromatiya/plymouth-theme-arch10)** by Mauro A. Meloni (GPL-2.0): boot splash base, modified for Angel OS
- **Linux Kernel Community**: the kernel

Arch Linux, KDE and all other names are trademarks of their respective owners. Angel OS is not affiliated with them.
