# REDACT 3

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Platform: Windows 10 / 11](https://img.shields.io/badge/Platform-Windows%2010%20%2F%2011-black.svg)]()
[![Architecture: 64--bit](https://img.shields.io/badge/Architecture-64--bit-critical.svg)]()

**REDACT 3** is an advanced, forensic-grade system artifact sanitization engine engineered for absolute data destruction and system baseline hygiene. Standard cleaning utilities operate superficially on user-accessible directory layers. REDACT 3 operates at the kernel-user space boundary, interacting directly with low-level system forensic markers, restricted registry hives, filesystem transition journals, and volatile memory allocations.

Designed with a high-end, futuristic **Windows 11 Fluent Dark UI**, it balances extreme data-erasure capabilities with an elegant, scannable, toggle-driven dashboard.

---

##  KEY HARDENING FEATURES (ANTI-FORENSIC BASELINE)

REDACT 3 implements dedicated architectural countermeasures engineered to safeguard memory state integrity and disrupt live physical triage harvesting strings:

*   **Transient Execution Splitting (Memory Obfuscation):** On initialization, the binary automatically clones its execution thread into an isolated, randomized transient process context inside secure temporary staging paths. This splits the execution chain from static application names, cleanly bypassing endpoint logging frameworks (**Prefetch, BAM, and AmCache**).
*   **Zero-Footprint Volatile Flow:** The tool operates entirely on an in-memory execution loop. It does not write local log files, debugging reports, or secondary text tracks to local storage.
*   **Blind Memory Security:** Plaintext path strings are explicitly prohibited from surviving execution scopes or compiling into an unmanaged text roadmap. Real-time stats are tracked strictly via transient integer tokens, neutralizing the risk of string carving from a live physical RAM dump.
*   **NTFS Cliff Protection (Sequential Overwrite Padding):** To mask sudden deletion transaction drops in the NTFS master tables, the engine automatically injects a controlled cluster burst of dummy transactions post-clean, blending deletion activity seamlessly into ambient OS storage traffic.
*   **Registry Parent Key Modification Forcing:** REDACT 3 forces structural parameter rotations over parent registry key containers, causing hidden `LastWrite` timestamps to roll over and obscuring the timeline of deleted sub-keys.

---

##  THE 250 DISCRETE TARGET TOOL MATRIX

The engine processes exactly **250 highly specialized system target nodes** distributed across three operational severity bands:

### Tier 1: Low Sensitivity (60 Items)
*Cache sweeps, temporary environment normalization, and transient layout debris.*
*   **Volatile Windows Temp Channels:** Sweeps all system-wide `C:\Windows\Temp\*` and individual user `%TEMP%\*` staging directories.
*   **Shell Previews & Graphic Buffers:** Obliterates thumbnail databases (`thumbcache_*.db`) and custom icon arrangement layouts (`iconcache_*.db`).
*   **Diagnostics & Hotfix Leftovers:** Purges Windows Error Reporting queues (`WER\ReportQueue`), analytical telemetry staging, and staged update payload pools (`SoftwareDistribution\Download`).

### Tier 2: Medium Sensitivity (70 Items)
*Application tracking lifecycles, active development staging pools, and full browser operations tracking profiles.*
*   **Shell Activity Ledgers:** Clears address bar typing histories, recently opened folders, and taskbar right-click jump lists (`AutomaticDestinations`).
*   **Administrative Instrumentation Logs:** Invokes automated high-privilege parameters to fully drop Windows Event Logs via `wevtutil` (Application, System, Security, Setup, and PowerShell Operational streams).
*   **Developer Workspace States:** Erases multi-tab recovery schemas, package buffers, and workspace tracking profiles inside VS Code, npm, Pip, Go, Unity, Blender, and Android Studio.
*   **The 10-Browser Web Matrix:** Securely purges cache repositories, indexed databases, site permissions, and tracking cookies across ten sovereign browser environments: Google Chrome, Microsoft Edge, Mozilla Firefox, Brave, Comet AI, Vivaldi, Arc, Zen, Pale Moon, and Tor Browser.

### Tier 3: High Sensitivity (120 Items)
*Structural operating system database monoliths, cryptographic authentication vaults, and filesystem master transaction journals.*
*   **The Big Three Forensics Monoliths:** Neutralizes the ultimate execution trackers: the **AmCache Hive** (`Amcache.hve`), the **AppCompatCache** (`Shimcache`), and the **Background Activity Monitor (BAM)**.
*   **Filesystem Structural Journals:** Truncates and deletes the NTFS Change Journal (`$UsnJrnl`), master filesystem transition tables (`$LogFile`), and transactional resource management streams (`$Txf`) to break deleted filename carving loops.
*   **Exotic Hardware History Matrices:** Targets low-level registry nodes to wipe all identifying vendor strings, model configurations, and first/last connectivity tracking lines for attached storage letters (`MountedDevices`) and USB peripherals (`USBSTOR`).
*   **AI Timeline Capture Pools:** Destroys local semantic database nodes and continuously captured image snapshot clusters mapping active terminal layouts inside the native **Windows Recall (CoreAI)** architecture.
*   **Shadow Frame Snapshots:** Programmatically purges and terminates all volume recovery states and system backup boundaries (Volume Shadow Copies / VSS) across all online physical hard drives.

---

##  COMPILATION & INSTALLATION

REDACT 3 is built entirely in pure Python using native Win32 API hooks to remain highly lightweight, independent, and free of external runtime dependencies. 

To package the tool into a clean, zero-dependency standalone binary executable embedded with your custom application icon, execute the following PyInstaller directive from an elevated command terminal:

```bash
pyinstaller --onefile --windowed --uac-admin --icon=logo.ico REDACT.py
