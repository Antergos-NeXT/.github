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
- The **Calamares installer** — mature, upstream-supported, offline + online modes
- The spirit of an Arch Linux live environment that just works
- **Community-driven development** — contributions welcome

## 🟢 What's new or changed

- **Artix Linux** base with **OpenRC** instead of Arch/systemd
- **Calamares** as the primary installer — offline (KDE squashfs) + online (netinstall with multiple DEs), OpenRC services configured
- **KDE Plasma** as the default desktop environment (GNOME removed — systemd dependency)
- **buildiso (artools)** for ISO builds
- **Modern CI** — all packages auto-built and deployed to gh-pages
- **Antergos branding** throughout — about dialog, installer theme, default branding fallback

## 🟡 What's not coming back

❌ 1:1 replica of the original ISO — ❌ Cnchi (retired — too unstable to maintain) — ❌ Unmaintainable packages — ❌ Outdated design choices — ❌ The old GTK3 Cnchi — ❌ systemd — ❌ Anything that belongs in a different era

If you came looking for a museum piece, you're in the wrong place. This is forward, not backward.

## 🐧 Why OpenRC?

Antergos NeXT is migrating *away* from systemd to OpenRC. Here's why:

- **systemd is an ever-growing monolith** — it started as an init system, now it controls logind, resolved, timedated, homed, journald, networkd, and is pushing age verification fields into the OS. It has abandoned the Unix philosophy of doing one thing well.
- **GNOME became a systemd hostage** — GNOME 49+ dropped non-systemd code paths entirely, making it impossible to run GNOME without systemd. Artix Linux dropped GNOME for this reason in 2025.
- **We don't trust systemd's trajectory** — the project has grown beyond init into a full OS management suite with no accountability, no modularity, and an ever-expanding scope that belongs in userspace, not PID 1.
- **Systemd's age verification** — [PR #40954](https://github.com/systemd/systemd/pull/40954) (merged Mar 2026) added an optional `birthDate` field to userdb JSON records for age verification compliance with California, Colorado, and Brazil laws. Optional today — precedent tomorrow. This is not the future Antergos wants.
- **systemd 260 (March 2026) dropped SysV init support entirely** — `systemd-sysv-generator`, `rc-local.service`, and all legacy compatibility code removed. No fallback. If your distro isn't 100% systemd-native, it breaks. We'd rather not tie our distro to that trajectory.

> To the users who loved Antergos with systemd — we know this isn't what you signed up for. The original Antergos ran on systemd, and we wanted to keep it that way. But systemd's direction left us with no choice. Blame upstream, not us.

---

## Repos

| Repo | Description |
|------|-------------|
| [**antergos-iso**](https://github.com/Antergos-NeXT/antergos-iso) | Live ISO build — Artix Linux, KDE Plasma, Calamares, OpenRC |
| [**antergos-packages**](https://github.com/Antergos-NeXT/antergos-packages) | Custom package repository with CI |
| [**cnchi-next**](https://github.com/Antergos-NeXT/cnchi-next) | Graphical installer for Arch Linux — GTK4 fork (maintained separately) |
| [**antergos-welcome**](https://github.com/Antergos-NeXT/antergos-welcome) | Welcome screen for Antergos NeXT live ISO |

### Package list

| Package | Type |
|---------|------|
| `calamares` | Universal installer (forked — Antergos NeXT branding, OpenRC module enabled) |
| `calamares-branding-antergos-next` | Calamares theme |
| `antergos-next-keyring` | GPG keyring |
| `antergos-next-mirrorlist` | Mirror config |
| `antergos-next-desktop-settings` | GTK/Plasma theme defaults |
| `antergos-next-memes` | Mix of audios for misc things — may or may not be used, we don't know |
| `antergos-wallpapers` | Desktop wallpapers |
| `yay` | AUR helper |
| `downgrade` | Package downgrade tool |

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

- **Base**: Artix Linux with OpenRC
- **ISO build**: `buildiso` (artools) with custom pacman config and package overlay
- **Installer**: Calamares (Qt6, C++, KDE offline + online netinstall with multiple DEs, OpenRC services support)
- **Desktop**: KDE Plasma (default)
- **Init**: OpenRC (no systemd)
- **Boot**: GRUB (BIOS + UEFI)
- **Packaging**: All custom packages built via GitHub Actions, hosted on gh-pages
- **Repo layout**: Flat URL (`https://antergos-next.github.io/antergos-packages/`) — no arch subdirectory
- **Signing**: Packages currently unsigned (no secret key in CI) — keyring package exists for future use
- **Easter egg**: CHANNEL 666 — type 666 three times for a special experience
- **Maintainer**: Solo (Celestia Ludenberg), recovering from ankle injury — updates may be slow

</details>

---

## This project is **not affiliated with, endorsed by, or connected to** the original Antergos project or its developers. It is an independent effort built upon the legacy of Antergos, not a sanctioned continuation.

---

<p align="center"><sub><i>Maintained solo by Celestia Ludenberg. Updates may be slow — be patient, or better yet, contribute.</i></sub></p>

<p align="center"><sub><i>If you came here thinking this is a direct revival of the original Antergos, you were mistaken lol. Antergos NeXT is a modernization project — what comes back does so on our terms, not as a museum replica. Not everything returns, and that's intentional.</i></sub></p>
