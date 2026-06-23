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
- The **Cnchi installer** (now ported to **GTK4**)
- The spirit of an Arch Linux live environment that just works
- **Community-driven development** — contributions welcome

## 🟢 What's new or changed

- **GTK4 port** of Cnchi — modern toolkit, not the old GTK3
- **Calamares** as an experimental secondary installer — offline (GNOME squashfs) + online (8 DEs via netinstall), dracut initramfs
- **Channel 666 easter egg** — type `666` three times during installation
- **Antergos NeXT memes** package — audio files for easter eggs
- **Modern CI** — all packages auto-built and deployed to gh-pages
- **Light blue theme**, updated wallpapers, GNOME default DE
- **Sudo -E** launcher instead of pkexec for Cnchi (wheel NOPASSWD)

## 🟡 What's not coming back

❌ 1:1 replica of the original ISO — ❌ Unmaintainable packages — ❌ Outdated design choices — ❌ The old GTK3 Cnchi — ❌ Anything that belongs in a different era

If you came looking for a museum piece, you're in the wrong place. This is forward, not backward.

---

## Repos

| Repo | Description |
|------|-------------|
| [**Antergos-NeXT-ISO**](https://github.com/Antergos-NeXT/antergos-iso) | Live ISO build — Arch Linux, GNOME, Cnchi installer |
| [**Cnchi**](https://github.com/Antergos-NeXT/cnchi-next) | GTK4 graphical installer (cnchi-dev branch) |
| [**antergos-packages**](https://github.com/Antergos-NeXT/antergos-packages) | Custom package repository with CI |

### Package list

| Package | Type |
|---------|------|
| `cnchi` | Graphical installer |
| `calamares` | Universal installer (experimental) |
| `calamares-branding-antergos-next` | Calamares theme |
| `hal` | HAL 9000 package manager — dual-mode, native dep resolver |
| `antergos-next-keyring` | GPG keyring |
| `antergos-next-mirrorlist` | Mirror config |
| `antergos-next-desktop-settings` | GTK/Plasma theme defaults |
| `antergos-next-memes` | Easter egg audio |
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

<details>
<summary><b>🔧 Technical details</b></summary>

- **ISO build**: `mkarchiso` (archiso) with `./prepare.sh && sudo ./mkarchiso -v .`
- **Installer**: Cnchi (GTK4, Python), Calamares (Qt6, C++, offline GNOME + online netinstall with 8 DEs, dracut)
- **Session type**: Live environment with `archiso` + `systemd-boot`
- **Desktop**: GNOME (default), KDE Plasma available
- **Packaging**: All custom packages built via GitHub Actions, hosted on gh-pages
- **Signing**: Packages currently unsigned (no secret key in CI) — keyring package exists for future use
- **Easter egg**: CHANNEL 666 — type 666 three times for a special experience
- **Maintainer**: Solo (Celestia Ludenberg), recovering from ankle injury — updates may be slow

</details>

---

## This project is **not affiliated with, endorsed by, or connected to** the original Antergos project or its developers. It is an independent effort built upon the legacy of Antergos, not a sanctioned continuation.

---

<p align="center"><sub><i>Maintained solo by Celestia Ludenberg. Updates may be slow — be patient, or better yet, contribute.</i></sub></p>

<p align="center"><sub><i>If you came here thinking this is a direct revival of the original Antergos, you were mistaken lol. Antergos NeXT is a modernization project — what comes back does so on our terms, not as a museum replica. Not everything returns, and that's intentional.</i></sub></p>
