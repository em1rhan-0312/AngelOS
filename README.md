<div align="center">
  <img src="docs/logo.png" width="96" alt="Angel OS logo"/>
  <h1 align="center">Angel OS</h1>
  <p align="center"><b>Fly With Your Angel</b></p>
  <p align="center">A clean, fast and ready-to-use Linux distribution with a graphical installer, a complete office and development toolkit, and its own identity.</p>
  <p align="center">
    <a href="https://claude.ai/artifact/PzL9zfNfjpqzN31AfZCobc">Website</a> ·
    <a href="https://instagram.com/angel0sofficial">Instagram</a> ·
    <a href="https://gitlab.com/emirhan.0312">GitLab</a> ·
    <a href="https://github.com/valkyrie-0312">GitHub</a>
  </p>
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
- [Support & Community](#support--community)
- [Credits](#credits)
- [License](#license)

## Overview

Angel OS is a rolling-release distribution built to be installed in minutes and used right away. You get a polished desktop, an installer that does not ask technical questions you do not care about, and a software selection that covers work, study and everyday use out of the box.

> [!NOTE]
> Angel OS is in **alpha**. The first public ISO is being prepared; follow the official Instagram account for the announcement.

## Features

### Installer

- Graphical installer (Calamares) with Angel OS branding
- Welcome screen written in 12 languages
- Steps: language, time zone, keyboard, disk, user, summary
- One desktop, no questions about it
- Online install: the newest packages are downloaded during setup

### Desktop and Look

- KDE Plasma desktop with the Angel OS application launcher
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
| **Creative** | ArtCraft Launcher (installs and starts the ArtCraft apps; early builds) |
| **System** | Konsole, KCalc, KDE Partition Manager, Timeshift (backups), htop, fastfetch |

> [!TIP]
> The Visual Studio Code in the repositories is the open-source **Code - OSS** build. Some Microsoft-only extensions are not available in it; the rest of the extension ecosystem works through Open VSX.

### Angel Welcome

The welcome window opens at the first start and gives you quick access to:

- Install Angel OS (live session only)
- Update system
- Install extra kernels
- Open the ArtCraft Launcher
- Settings, terminal, browser
- Community links

Untick *Show this window at startup* to hide it on an installed system. Start it again any time from the application menu.

## Download

| File | SHA256 |
| :--- | :--- |
| `angel-os-YYYY.MM.DD-x86_64.iso` | _add link and checksum when the ISO is published_ |

Verify your download:

```bash
sha256sum angel-os-*.iso
```

## System Requirements

| | Minimum | Recommended |
| :--- | :--- | :--- |
| CPU | 64-bit (x86_64) | 64-bit, 2+ cores |
| RAM | 2 GB | 4 GB |
| Disk | 20 GB | 40 GB |
| Network | Required for installation | Wired or Wi-Fi |

## Installation

1. Write the ISO to a USB drive (Ventoy, balenaEtcher, or `dd`) and boot from it.
2. The live desktop starts automatically. Open **Install Angel OS** from the welcome window or the desktop.
3. Follow the installer: language, time zone, keyboard, disk, user, summary.
4. Wait for the system to download and install, then reboot.

### Virtual Machine

Recommended VirtualBox settings:

- 4 GB RAM, 2 or more CPU cores
- Enable **EFI** under System
- Display: **VMSVGA**, 128 MB video memory, 3D acceleration **off**
- 30 GB or more of virtual disk for a full install

## Kernels

The standard `linux` kernel is installed by default. Additional kernels are available from the repositories and can be added at any time (the Angel Welcome window has a shortcut):

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

You need an Arch Linux machine or VM with about 25 GB of free space.

```bash
sudo pacman -S archiso git base-devel
git clone https://gitlab.com/emirhan.0312/angel-os.git
cd angel-os
chmod +x build.sh
sudo ./build.sh        # run with sudo from your normal user, not as root directly
```

The ISO is written to `out/`. The first build is slow because the installer is compiled from the AUR; compiled packages are cached in `localrepo/`, so later builds are faster.

## Project Layout

```
angel-os/
├── build.sh                  # builds the ISO
├── repo/                     # Angel OS pacman repository (PKGBUILDs + build script)
├── .gitlab-ci.yml            # publishes the repository with GitLab Pages
├── overlay/
│   ├── packages.extra        # software included on the ISO
│   ├── boot/splash.png       # boot menu background
│   └── airootfs/             # files copied into the live system
└── ROADMAP.md
```

## Roadmap

- [x] Branding: name, logo, boot splash, wallpapers, terminal logo
- [x] Office and development software
- [x] Angel Welcome
- [x] Repository tooling (`repo/`)
- [ ] Installer polish and real-hardware testing
- [ ] Publish the `[angel]` repository
- [ ] Signed packages
- [ ] Automated builds and version numbers
- [ ] Offline installation

See [ROADMAP.md](ROADMAP.md) for details.

## Support & Community

- **Instagram (official):** [@angel0sofficial](https://instagram.com/angel0sofficial)
- **Developer:** [@_e0312](https://instagram.com/_e0312) · [GitLab](https://gitlab.com/emirhan.0312) · [GitHub](https://github.com/valkyrie-0312)
- **Email:** jinglelot@gmail.com

Bug reports and ideas are welcome as issues on GitLab.

## Credits

Angel OS is an independent project, built on the work of many others:

- **[Arch Linux](https://archlinux.org)** and **[archiso](https://gitlab.archlinux.org/archlinux/archiso)**: foundation distribution and ISO tooling
- **[KDE](https://kde.org)**: Plasma desktop and applications
- **[Calamares](https://calamares.io)**: installer framework (GPL-3.0-or-later)
- **[LibreOffice](https://www.libreoffice.org)**, **[Code - OSS](https://github.com/microsoft/vscode)**, **[Firefox](https://www.mozilla.org/firefox/)** and the many other open-source projects shipped on the ISO
- **[plymouth-theme-arch10](https://github.com/eromatiya/plymouth-theme-arch10)** by Mauro A. Meloni (GPL-2.0): boot splash base, modified for Angel OS
- **Linux Kernel Community**: the kernel

Arch Linux, KDE and all other names are trademarks of their respective owners. Angel OS is not affiliated with them.

## License

Add a `LICENSE` file before publishing (GPL-3.0 is the usual choice for a distribution project). Third-party components keep their own licenses.
