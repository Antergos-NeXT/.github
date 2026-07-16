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

Antergos NeXT has migrated *away* from systemd. We default to Dinit, with OpenRC, Runit, and S6 available. Here's why:

- **systemd is an ever-growing monolith** — it started as an init system, now it controls logind, resolved, timedated, homed, journald, networkd, and is pushing age verification fields into the OS. It has abandoned the Unix philosophy of doing one thing well.
- **GNOME became a systemd hostage** — GNOME 49+ dropped non-systemd code paths entirely, making it impossible to run GNOME without systemd. Artix Linux dropped GNOME for this reason in 2025.
- **We don't trust systemd's trajectory** — the project has grown beyond init into a full OS management suite with no accountability, no modularity, and an ever-expanding scope that belongs in userspace, not PID 1.
- **Systemd's age verification** — [PR #40954](https://github.com/systemd/systemd/pull/40954) (merged Mar 18, 2026 by bluca) added a `birthDate` field to userdb records for age compliance (California AB-1043, Colorado SB26-051, Brazil Lei 15.211/2025). Someone tried to [revert it](https://github.com/systemd/systemd/pull/41179) the next day. Didn't matter. Poettering personally closed the revert, locked the PR as "too heated," limited conversation to collaborators, and told everyone they were "misunderstanding what systemd does here." The field is still in the codebase. Optional today, precedent tomorrow. They're not sorry. They're waiting.  
  Think about it: an **init system** now has a standardized field for your date of birth. Not a login manager. Not a user profile daemon. PID 1 knows when you were born. That's not a bug — that's a feature they intentionally designed, reviewed, and merged.
- **systemd 260 (March 2026) dropped SysV init support entirely** — `systemd-sysv-generator`, `rc-local.service`, and all legacy compatibility code removed. No fallback. If your distro isn't 100% systemd-native, it breaks. We'd rather not tie our distro to that trajectory.
- **systemd complains about services you never asked for** — install a clean Arch system, don't touch any optional services, and systemd will still nag you about `something.service` failing to start because it was *ConditionalExec*=*d* but not *enabled*. Optional services should be *optional*, not something the init system whines about at boot. We don't need an init system that nags. We need one that shuts up and runs what we tell it to.

- **Could we go back to Arch?** `archiso` still works. The `before-systemd-change` branch in [antergos-iso](https://github.com/Antergos-NeXT/antergos-iso/tree/before-systemd-change) is literally the old systemd-based profile — it's right there, untouched, waiting. The profile could target Arch instead of Artix with about a weekend of work. The packages would build fine. We know the workflow. It would be easy. We could do it.  
  **We won't.** Artix gave us init freedom without a fight. Arch gave us systemd and said "deal with it." We chose the fork in the road that doesn't lead to a monopoly. This isn't about what's easier — it's about what's right for the project's future. If you want Arch with Antergos branding, the source is right there. Fork it. We mean that genuinely.  
  That said, if you want to stay on Arch/systemd but ditch the age verification baggage, there's [`systemd-liberated-git`](https://aur.archlinux.org/packages/systemd-liberated-git) on AUR — a community fork that strips the birthDate and surveillance-adjacent features. Not our path, but it exists if you need it.

> To the users who loved Antergos with systemd — we know this isn't what you signed up for. The original Antergos ran on systemd, and we wanted to keep it that way. But systemd's direction left us with no choice. Blame upstream, not us.

> **Wait, Dinit? What happened to OpenRC?** We shipped OpenRC. Then Calamares kidnapped pacman's resolver. Every `--noconfirm` call picked `elogind-dinit` (alphabetically before `elogind-openrc`), pulling in `dinit-rc` which conflicts with `openrc`. We tried `--ignore` — pacman ignored it. We tried `--assume-installed=init-logind` — ALPM doesn't check those for virtual providers. We tried `--ask=12` — infinite loop (pacman kept re-adding `elogind-dinit`). We tried a dummy package in a custom repo. Pacman laughed at all of them. Dinit works great, and OpenRC's service enabling is broken on installed systems anyway. Don't blame us, blame alphabetical order.

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

- **Base**: Artix Linux with Dinit (default) / OpenRC / Runit / S6
- **ISO build**: `buildiso` (artools) with custom pacman config and package overlay
- **Installer**: Calamares (Qt6, C++, online netinstall with multiple DEs, Dinit only)
- **Desktop**: KDE Plasma (default)
- **Init**: Dinit (switch to OpenRC/Runit/S6 via changing-init.md)
- **Boot**: GRUB (BIOS + UEFI)
- **Packaging**: All custom packages built via GitHub Actions, hosted on gh-pages
- **Repo layout**: Flat URL (`https://antergos-next.github.io/antergos-packages/`) — no arch subdirectory
- **Signing**: Packages currently unsigned (no secret key in CI) — keyring package exists for future use
- **Easter egg**: CHANNEL 666 — type 666 three times for a special experience
- **Maintainer**: Solo (Michał), recovering from ankle injury — updates may be slow

</details>

---

## This project is **not affiliated with, endorsed by, or connected to** the original Antergos project or its developers. It is an independent effort built upon the legacy of Antergos, not a sanctioned continuation.

---

<p align="center"><sub><i>Maintained solo by Michał. Updates may be slow — be patient, or better yet, contribute.</i></sub></p>

<p align="center"><sub><i>If you came here thinking this is a direct revival of the original Antergos, you were mistaken lol. Antergos NeXT is a modernization project — what comes back does so on our terms, not as a museum replica. Not everything returns, and that's intentional.</i></sub></p>
