# PulseDesk releases

PulseDesk is a Windows hardware-monitoring application for keeping an eye on CPU, GPU, memory and storage readings. This public distribution repository contains installers, release notes and public update metadata.

## Download and install

**[Download the latest PulseDesk release](https://github.com/FuegoRoseAI/PulseDesk-Releases/releases/latest)**

1. Open the latest Release page. The current stable release is **v1.0.4**; download **[PulseDesk-1.0.4-Setup.exe](https://github.com/FuegoRoseAI/PulseDesk-Releases/releases/download/v1.0.4/PulseDesk-1.0.4-Setup.exe)**.
2. Save any active recording and close PulseDesk normally before a manual upgrade.
3. Run the installer, follow Setup, then open PulseDesk from the Start menu.

Requires **64-bit Windows 10/11 and .NET Framework 4.8 or later**. Setup installs for the current Windows user, by default under `%LOCALAPPDATA%\Programs\PulseDesk`. It does not install .NET, drivers or services.

Saved preferences and recordings are kept separately under `%LOCALAPPDATA%\PulseDesk` and preserved during upgrades and uninstall. Setup does not rewrite existing recordings or force-close the running application. In-app updates stop and save an active recording before installation; recording does not resume automatically afterward.

**Versions through 1.0.3 require one manual installation of the configured [1.0.4 build](https://github.com/FuegoRoseAI/PulseDesk-Releases/releases/tag/v1.0.4) before online updates work.** Those older builds cannot discover the new update endpoint and verification key automatically.

## Features

- **Live hardware monitoring:** available CPU/GPU readings, Windows memory metrics and storage readings, with component details and charts.
- **Overview and Compact modes:** a dashboard and a smaller desktop window with configurable readings, recording controls and an opt-in, saved **Always on top** setting.
- **Recording and CSV export:** timestamped Live/Demo sessions, saved-session summaries, reopening and CSV export. Unavailable readings remain distinguishable from measured values.
- **Saved preferences:** layout, refresh interval, Compact placement and selection of a detected GPU.
- **Sensor diagnostics:** inspect detected devices, sensor sources and availability. **Demo Mode** is an explicitly selected simulated-data fallback.

## Updates

Open **Preferences → About → Check for Updates** in the installed application. Checks are manual; PulseDesk does not check at startup or silently download or install updates.

If a newer version is offered, review its release notes and choose **Download and Install**. Downloads can be canceled. After verification, a separate confirmation is required before installation. PulseDesk saves settings and any active recording, stops monitoring, opens visible Setup and reopens afterward.

Public stable feed: **[manifest.json](https://github.com/FuegoRoseAI/PulseDesk-Releases/releases/latest/download/manifest.json)**

The manifest contains an embedded RSA-3072/SHA-256 signature, verified against the application's built-in public key. Its signed payload authenticates the release version, release notes, installer URL, byte size, SHA-256 and validity timestamps. The updater verifies the downloaded installer's size and SHA-256 before allowing installation and rejects invalid or expired metadata. No detached signature file or GitHub login is required.

Metadata expires 30 days after signing and must be refreshed by the publisher before expiry. The published 1.0.4 metadata expires **November 25, 2026, at 11:25 UTC**; expired metadata blocks updating rather than bypassing verification.

**Metadata signing is not Windows Authenticode signing.** The current 1.0.4 application and installer are not Authenticode signed. Keep Windows security protections enabled and review normal Windows prompts.

## Sensor access

PulseDesk uses **LibreHardwareMonitor 0.9.6** and Windows metrics. Some CPU temperature, clock, power and motherboard readings require the separately installed **official signed PawnIO edition** and administrator access. The current backend uses **PawnIO 2.2.0**; PulseDesk Setup does not install or update it.

Start PulseDesk normally and select **Live Mode**. If **Sensor diagnostics** reports denied access, the explained **Restart as administrator** action lets you explicitly approve Windows UAC. Administrator access cannot supply a missing driver or unsupported sensor. After an update, additional CPU/board readings may require this explicit restart again.

Missing, unsupported, denied or stale readings show **N/A** with availability feedback; Live Mode never silently substitutes simulated data. Sensor availability depends on hardware, drivers and permissions. Universal hardware support and guaranteed compatibility with Vanguard or other anti-cheats are not claimed. Compact mode is an ordinary desktop window; visibility over exclusive fullscreen games is not guaranteed.

## Repository scope

This repository distributes PulseDesk installers and public signed update metadata. **Private signing keys, credentials, application source, recordings and user settings do not belong here.** Required third-party notices, licenses and corresponding dependency source archives are included with the installer.

GitHub-generated **Source code (zip/tar.gz)** downloads contain this distribution repository, **not PulseDesk's application source**.
