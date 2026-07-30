<!--
Antergos NeXT org profile
Uses picture + prefers-color-scheme for light/dark aware header banner
-->

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="img/banner-dark.svg">
    <img src="img/banner-light.svg" alt="Antergos NeXT banner" width="720">
  </picture>
</p>

> *"I think it's fine so long as it's clear that your project is your own and not affiliated with the original. Have fun!"* — Dustin (original Antergos founder)

---

## 🔵 What's back

- The **Antergos name** and **logo**
- The **Calamares installer** — mature, upstream-supported, online mode (BYODE script for bare-system offline installs)
- The spirit of an Arch Linux live environment that just works
- **Community-driven development** — contributions welcome

## 🟢 What's new or changed

- **Artix Linux** base with **Dinit** (switchable via changing-init.md) instead of Arch/systemd
- **Calamares** as the primary installer — online (netinstall with multiple DEs) + BYODE offline script
- **KDE Plasma** as the default desktop environment (GNOME removed — systemd dependency)
- **buildiso (artools)** for ISO builds
- **Modern CI** — all packages auto-built and deployed to gh-pages
- **Antergos branding** throughout — about dialog, installer theme, default branding fallback
- **Antergos Layan theme** — Kvantum, SDDM, GRUB theme, plasma plasmoids, Konsole, Yakuake skin

## 🟡 What's not coming back

❌ 1:1 replica of the original ISO — ❌ Cnchi (retired — too unstable to maintain) — ❌ Unmaintainable packages — ❌ Outdated design choices — ❌ The old GTK3 Cnchi — ❌ systemd — ❌ Anything that belongs in a different era

If you came looking for a museum piece, you're in the wrong place. This is forward, not backward.

## 🐧 Why not systemd?

Antergos NeXT uses Dinit — it's lightweight, fast, and stays out of the way. Artix provides Dinit, OpenRC, Runit, and S6; we chose Dinit as the supported default because OpenRC has service-enable bugs on installed systems. You can switch to another init via [`changing-init.md`](https://github.com/Antergos-NeXT/antergos-iso/blob/master/docs/changing-init.md) in the ISO repo.

---

## Repos

| Repo | Description |
|------|-------------|
| [**antergos-iso**](https://github.com/Antergos-NeXT/antergos-iso) | Live ISO build — Artix Linux, KDE Plasma, Calamares, Dinit |
| [**antergos-packages**](https://github.com/Antergos-NeXT/antergos-packages) | Custom package repository with CI |
| [**cnchi-next**](https://github.com/Antergos-NeXT/cnchi-next) | Graphical installer for Arch Linux — GTK4 fork (unmaintained, kept for reference) |
| [**antergos-welcome**](https://github.com/Antergos-NeXT/antergos-welcome) | Welcome screen for Antergos NeXT live ISO |

### Package list

| Package | Type |
|---------|------|
| `calamares` | Universal installer (upstream, packaged as-is) |
| `calamares-branding-antergos-next` | Calamares theme |
| `antergos-next-keyring` | GPG keyring |
| `antergos-next-mirrorlist` | Mirror config |
| `antergos-next-desktop-settings` | GTK/Plasma theme defaults |
| `antergos-plasma-theme` | Plasma desktop theme (dark), look-and-feel, splash screen |
| `antergos-sddm-theme` | SDDM login theme with built-in background |
| `antergos-wallpapers` | Desktop wallpapers |
| `yay` | AUR helper |
| `downgrade` | Package downgrade tool |
| `antergos-layan-theme` | Layan theme suite (Kvantum, SDDM, plasmoids, Konsole, Yakuake) |
| `antergos-grub-theme` | GRUB theme (Layan, 75 distro icons, Antergos wallpaper) |

---

<details>
<summary><b>📜 Fun fact — the name saga</b></summary>

This project launched as **Antergos NeXT** — a direct nod to the original. After a takedown request from a former dev (who was not Dustin), it was temporarily renamed to **Pulsar Linux** to avoid legal headache. But when Dustin Falgout — one of the three original Antergos founders — heard about it, he gave his explicit blessing to use the Antergos name:

> *"I think it's fine so long as it's clear that your project is your own and not affiliated with the original. Have fun!"*

So we switched back. Pulsar Linux continues as a [separate project](https://github.com/Pulsar-Linux) under its own identity.

</details>

> **⚠️ To any press reading this:** If you see an article claiming Antergos NeXT is abandoned, it's outdated. During the brief rename to *Pulsar Linux* (before Dustin's blessing came through), some outlets assumed the project died. It didn't. Name changed back, installer got upgraded, development is active. Check the commit history.

<details>
<summary><b>🔧 Technical details</b></summary>

- **Base**: Artix Linux with Dinit (default + only init)
- **ISO build**: `buildiso` (artools) with custom pacman config and package overlay
- **Installer**: Calamares (Qt6, C++, online netinstall with multiple DEs)
- **Desktop**: KDE Plasma (default)
- **Init**: Dinit (switch to OpenRC/Runit/S6 via changing-init.md)
- **Boot**: GRUB (BIOS + UEFI)
- **Packaging**: All custom packages built via GitHub Actions, hosted on gh-pages
- **Repo layout**: Flat URL (`https://antergos-next.github.io/antergos-packages/`) — no arch subdirectory
- **Signing**: Commits GPG-signed with `F1D8F02C5E929F3FE0424EE897F813D238CF0DBB`. Packages unsigned by design — avoids Manjaro-style GPG expiry lockouts on `pacman -Syu`.
- **Easter egg**: the synthwave wallpaper
- **Maintainer**: Solo (Michał), recovering from ankle injury — updates may be slow

</details>

---

## This project is **not affiliated with, endorsed by, or connected to** the original Antergos project or its developers. It is an independent effort built upon the legacy of Antergos, not a sanctioned continuation.

---

<p align="center"><sub><i>Maintained solo by Michał. Updates may be slow — be patient, or better yet, contribute.</i></sub></p>

<p align="center"><a href="https://ko-fi.com/antergosnext"><img src="https://ko-fi.com/img/githubbutton_sm.svg" alt="ko-fi"></a></p>
