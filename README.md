<p align="center">
  <img src="logo.png" width="180"/>
</p>

<h1 align="center">REDACT 3</h1>

<p align="center">
  <i>ERASE EVERYTHING. LEAVE NOTHING.</i>
</p>

<p align="center">
  <b>250 targets · 3 tiers · 4 wipe standards · 10 browsers · Windows 11</b>
</p>

<p align="center">
  <a href="https://www.gnu.org/licenses/gpl-3.0.html"><img src="https://img.shields.io/badge/License-GPL%20v3-blue.svg"/></a>
  <img src="https://img.shields.io/badge/Platform-Windows%2010%20%2F%2011-black.svg"/>
  <img src="https://img.shields.io/badge/Architecture-64--bit-critical.svg"/>
  <img src="https://img.shields.io/badge/Python-3.9%2B-yellow.svg"/>
  <a href="https://sourceforge.net/projects/redact/"><img src="https://img.shields.io/badge/SourceForge-redact-orange?logo=sourceforge"/></a>
</p>

<p align="center">
  <b>Author:</b> Yonas Abeselom &nbsp;|&nbsp; <a href="mailto:yonas_abeselom@protonmail.com">yonas_abeselom@protonmail.com</a> &nbsp;|&nbsp; <a href="https://github.com/yonasabeselom">github.com/yonasabeselom</a>
</p>

<p align="center">
  <b>⭐ If REDACT is useful to you, please star this repository — it helps other privacy-conscious users find it.</b>
</p>

---

## Download

📦 **[Download standalone .exe on SourceForge](https://sourceforge.net/projects/redact/)** — no Python installation required. Runs on any Windows 10 or 11 (64-bit) machine as Administrator.

Or run directly from source — see [Installation & Usage](#installation--usage) below.

---

## Screenshot

![REDACT 3](screenshot.png)

---

## Who is this for?

- **Privacy-conscious users** who want meaningful control over what Windows remembers about them
- **IT professionals and sysadmins** preparing machines for redeployment, resale, or handoff
- **Journalists, researchers, and activists** working in sensitive environments
- **Developers and power users** who understand what these artifacts contain and want them gone
- **Anyone donating or selling a PC** who wants to ensure personal data doesn't travel with it

> REDACT 3 is intended for use on machines you own or are authorised to manage. It is not intended for use in circumventing lawful investigations or any activity prohibited by law in your jurisdiction.

---

## Features

- **250 individually selectable sanitization targets** across 3 sensitivity tiers
- **4 cryptographic wipe standards** — from a fast 1-pass SSD-optimised wipe to the full 35-pass Gutmann method
- **10-browser coverage** — Chrome, Edge, Firefox, Brave, Vivaldi, Arc, Zen, Pale Moon, Tor, and Comet
- **Registry cleaning** with direct `winreg` access and `reg.exe` fallback
- **Windows Recall / CoreAI** database and screenshot store destruction
- **Real-time monitor** showing live file count, bytes freed, and progress
- **Safe Selection preset** — one click enables everything except irreversible high-risk items
- **No external dependencies** — pure Python standard library only
- **Auto-elevates** to Administrator via UAC on first launch

---

## Privacy Architecture

REDACT 3 includes three internal hardening measures designed to prevent the tool's own execution from leaving a recoverable trace:

- **Transient Execution Splitting** — On launch, if the executable name contains "REDACT", the process clones itself to a randomised temporary name and re-executes from there, reducing its visibility in process history logs (Prefetch, BAM).
- **NTFS File Cliff Masking** — After each wipe batch, the engine writes and immediately deletes a cluster of random dummy files, smoothing the deletion spike in NTFS metadata that would otherwise stand out in a forensic timeline.
- **Registry LastWrite Spoofing** — Before deleting a registry key, REDACT writes and removes a decoy value in the parent key, rolling its `LastWrite` timestamp forward and obscuring when the target subkey was actually removed.

---

## The 250-Target Matrix

Targets are organised into three tiers. Each item is individually togglable.

### 🟢 Tier 1 — Low Sensitivity (60 items)
Safe ephemeral caches that Windows rebuilds automatically. Zero functional impact when removed.

- Windows & user temp folders, Recycle Bin, thumbnail and icon caches
- Prefetch files, font cache, DirectX shader cache
- Windows Error Reports, update leftovers, Delivery Optimization cache
- Diagnostic logs, telemetry staging, speech model caches, and more

### 🟡 Tier 2 — Medium Sensitivity (69 items)
Application history, browser caches, and usage records. May reset UI preferences in affected apps.

- File Explorer recent files, jump lists, Run dialog history, clipboard history
- Windows Event Logs, PowerShell command history, Windows Search history
- Browser caches across all 10 supported browsers
- App histories for Teams, Discord, Zoom, Steam, Spotify, VS Code, Blender, Unity, and more
- Developer tool caches: npm, pip, Go build cache, Android Studio, Sublime Text

### 🔴 Tier 3 — High Sensitivity (121 items)
Primary forensic artifacts and OS-level databases. Review each item before selecting.

| Target | What it exposes |
|---|---|
| AmCache Hive | Every program ever installed or run |
| AppCompatCache (ShimCache) | Every executable ever launched |
| Background Activity Monitor (BAM) | Kernel-level execution timestamps |
| NTFS Change Journal (`$UsnJrnl`) | Every file operation ever — create, rename, delete |
| Volume Shadow Copies (VSS) | Snapshots investigators use to recover deleted files |
| Shell Bags | Every folder ever opened, including USB drives |
| UserAssist | Encrypted launch count for every application |
| SRUM Database | Per-app network and CPU usage over time |
| Windows Recall / CoreAI | AI-captured screenshots and semantic timeline database |
| USB Device History (USBSTOR) | Serial numbers of every USB ever plugged in |
| Browser histories & passwords | Chrome, Edge, Firefox, Brave, Vivaldi, Arc, Zen, and more |
| Windows Search Index | Text snippets from documents, including deleted ones |
| Hibernation File (`hiberfil.sys`) | Full RAM dump captured at sleep — may contain open docs and keys |

> ⚠️ Items such as the Downloads folder, saved Wi-Fi passwords, Volume Shadow Copies, and browser credential stores are **excluded from the Safe Selection preset** because their removal is irreversible. Select them only if you understand what they contain.

---

## Installation & Usage

**Requirements:** Python 3.9+, Windows 10 or 11 (64-bit), Administrator privileges.

```bash
# Run directly
python REDACT.py
```

REDACT 3 will auto-elevate via UAC if the current session lacks Administrator rights.

**To build a standalone executable:**

```bash
pip install pyinstaller
pyinstaller --onefile --windowed --uac-admin --icon=logo.ico REDACT.py
```

No pip packages are required to run the script itself — only PyInstaller is needed if you want to compile to `.exe`.

---

## Why REDACT vs Other Tools

| Feature | REDACT 3 | CCleaner | BleachBit |
|---|---|---|---|
| **Open source** | ✅ GPL v3 | ❌ Proprietary | ✅ GPL |
| **Forensic artifact targets** | ✅ 250 (AmCache, BAM, ShimCache, SRUM…) | ❌ Basic only | ⚠️ Limited |
| **Windows Recall / CoreAI** | ✅ | ❌ | ❌ |
| **Registry LastWrite spoofing** | ✅ | ❌ | ❌ |
| **NTFS File Cliff Masking** | ✅ | ❌ | ❌ |
| **Transient Execution Splitting** | ✅ | ❌ | ❌ |
| **4 cryptographic wipe standards** | ✅ | ❌ | ⚠️ Basic |
| **10-browser coverage** | ✅ | ⚠️ Partial | ⚠️ Partial |
| **No telemetry / phoning home** | ✅ | ❌ (Free tier) | ✅ |
| **No external dependencies** | ✅ | N/A | N/A |

REDACT 3 is the only open-source Windows privacy tool built specifically to defeat forensic analysis — not just free up disk space.

---

## Wipe Standards

| Mode | Passes | Description |
|---|---|---|
| **1-Pass Quick** | 1 | Single cryptographic random overwrite + TRIM. Recommended for SSDs. |
| **NIST 800-88** | 3 | Fixed-pattern sequence per NIST SP 800-88. Accepted by US government agencies. |
| **7-Pass Secure** | 7 | Alternating DoD 5220.22-M pattern. For sensitive unclassified material. |
| **35-Pass Gutmann** | 35 | 9 fixed-pattern passes + 26 CSPRNG passes. Maximum destruction. |

> Note: On NVMe/SSD drives, wear-levelling means multi-pass file wiping is not guaranteed to reach original physical cells. For solid-state media, the 1-Pass + TRIM method combined with full-drive encryption is the most reliable approach.

---

## Companion Tool — AAD-50

REDACT 3 handles **OS-level** privacy cleaning — files, caches, registry traces, browser history, forensic artefacts.

For **firmware-level NVMe drive sanitization** — full physical destruction of all NAND cells including over-provisioned zones, FTL mapping, and cryptographic keys — see the companion tool:

🔒 **[AAD-50 — Abeselom ASIC-Direct 50](https://github.com/yonasabeselom/aad50)** — 50-cycle, hardware-confirmed NVMe sanitization with SHA-256 audit chain and PDF Certificate of Destruction.

> Together, REDACT 3 + AAD-50 cover the full stack — from the Windows registry down to the raw NAND cells.

---

## Changelog

### v3 — July 2026

- Complete rewrite to zero-footprint architecture
- **250 sanitization targets** across 3 sensitivity tiers — up from previous versions
- **Windows 11 Fluent Dark UI** — per-item toggle switches across tier-grouped cards
- **Windows Recall / CoreAI** destruction added — AI screenshot store and semantic timeline database
- **Transient Execution Splitting** — process clones to randomised temp name on launch
- **NTFS File Cliff Masking** — dummy file cluster written and deleted after each wipe batch
- **Registry LastWrite Spoofing** — decoy value rolls parent key timestamp forward before deletion
- **4 wipe standards** — 1-Pass Quick, NIST 800-88, 7-Pass DoD, 35-Pass Gutmann
- **10-browser coverage** — Chrome, Edge, Firefox, Brave, Vivaldi, Arc, Zen, Pale Moon, Tor, Comet
- **Safe Selection preset** — one-click enables all non-irreversible items
- **Real-time monitor** — live file count and bytes freed during cleaning
- **Auto-UAC elevation** — no manual right-click required
- **No external dependencies** — pure Python standard library

---

## Contributing

Bug reports, target suggestions, and pull requests are welcome.

- **Bug reports:** Open a [GitHub Issue](https://github.com/yonasabeselom/redact/issues) with your Windows version, Python version, and the full error output.
- **New targets:** If you know of a forensic artefact not currently covered, open an issue describing the registry path or file location.
- **Contact:** [yonas_abeselom@protonmail.com](mailto:yonas_abeselom@protonmail.com)

---

## ⚠️ Disclaimer

REDACT 3 **permanently destroys data**. Wiped files cannot be recovered. Registry keys deleted by REDACT are gone. Volume Shadow Copies, once deleted, remove your ability to restore previous file versions.

Always ensure you have backups of anything you want to keep before running this tool. The author accepts no liability for data loss, system instability, or any other consequence arising from its use.

This software is provided as-is under the GNU General Public License (GPL) v3.

---

## License

GPL v3 — see [LICENSE](LICENSE) for full terms. Source code is free to use, modify, and redistribute under the GPL. Any derivative works must also be released under the GPL.
