# REDACT v1.0

<p align="center">
  <img src="logo.png" alt="REDACT Logo" width="200" height="200">
</p>

Platform: Windows 11
Language: Python
License: MIT

REDACT is an advanced forensic privacy eraser and system artifact sanitization utility designed for power users, system administrators, and cybersecurity professionals who require the absolute destruction of tracking data. 

Unlike standard consumer-grade utilities that merely clear surface-level browser caches or unallocated temporary directories, REDACT targets, overwrites, and permanently purges deep operating system tracking matrices, application footprints, and critical forensic log hives across 218 distinct parameters.

---

## Key Features

* 218 Deep Targets Matrix: Exhaustive automated sweeping across low, medium, and high-sensitivity system sectors that standard tools miss.
* 4 Cryptographic Wipe Standards: Integrated support for 1-Pass NVMe block clearing, NIST 800-88, 7-Pass Secure DoD, and 35-Pass Maximum Gutmann overwriting algorithms.
* Solid-State Drive Optimization: Leverages native PowerShell ReTrim calls to trigger controller-level block clearing, safely optimizing sanitization for SSD and NVMe media without degrading hardware lifespans.
* Forensic Ghost Trail Neutralization: Severs deep registry tracking keys including AmCache, BAM Background Activity Monitor, and ShimCache to wipe application execution history.
* Filesystem Transaction Cleansing: Wipes volatile NTFS Change Journals and filesystem transaction logs to permanently prevent filename and metadata recovery.
* Detailed Forensic Audit Logs: Generates a clean, transparent execution report exported directly to your Desktop upon completion, documenting every file purged and registry key severed.
* Asynchronous Multi-Threaded Processing: Runs the entire wiping engine on an isolated background thread, ensuring a smooth user experience with zero application lockups or interface freezing.
* Modern Windows 11 Visual Layout: Features a lightweight, completely transparent, custom-animated Fluent Dark theme.

---

## Deep Forensic Sanitization Matrix (218 Target Items)

REDACT operates across modular tiers to completely sever forensic execution signatures, tracking logs, and physical storage residues.

### Low Sensitivity (Items 1–60)
*Targets temporary system environments, local graphics pipelines, user-level caches, and basic application debris.*

* **Core System Temp Sectors:** `C:\Windows\Temp\*`, `%TEMP%\*`, and legacy extraction staging pools (`C:\*.tmp`).
* **Shell & UI Caches:** Explorer Thumbnail Cache (`thumbcache_*.db`), Icon Cache (`iconcache_*.db`), and Photo import staging tracks.
* **Diagnostic & Update Logs:** System Log Files (`C:\Windows\Logs\*`), Windows Error Reporting (`ReportQueue`), Delivery Optimization P2P network caches, and old Windows Update remnants (`SoftwareDistribution\Download`).
* **Application History MRUs:** Native application tracking arrays including Notepad (Windows 11 LocalState packages), MS Paint, WordPad, and Windows Media Player recent file lists.
* **Hardware & Driver Buffers:** DirectX Shader Cache (`D3DSCache`), Bluetooth telemetry state diagnostics, Print Spooler operational queues, and localized biometric sensor databases.

---

### Medium Sensitivity (Items 61–130)
*Targets application execution paths, automated web browser caches, development build environments, and communications infrastructure.*

* **Shell Navigation Trails:** File Explorer Quick Access Recent Files, taskbar Jump Lists, Run Dialog History (`Win+R`), and Address Bar explicitly typed folder paths.
* **System Logging Facilities:** Full clearance of core Windows Event Logs via `wevtutil` (Application, Security, System, Setup, and PowerShell Operational logs).
* **Browser Operational Caches:** Temporary cache trees, code caches, and transient session cookies across Google Chrome, Mozilla Firefox, Microsoft Edge, and Brave.
* **Development Workspace History:** VS Code workspace storage histories, Python Pip package caches, Node.js npm global staging pools, Go Language build cache nodes, and Android Studio/Unity Editor recent project lists.
* **Collaboration & Media Footprints:** Microsoft Teams, Zoom, Discord, Slack, and Skype system runtime caches, alongside VLC Player subtitle and recently parsed media histories.

---

### High Sensitivity (Items 131–218)
*Targets low-level operating system forensic artifacts, user identity structures, cryptographic security tokens, and physical filesystem change journals.*

* **Identity & Credential Databases:** Cryptographic vault tables from Windows Credential Manager, raw saved passwords, history files, and automated billing/autofill data across all primary chromium and gecko browsers.
* **Forensic Execution Registries:** Complete removal of `UserAssist` execution keys, deep system `ShellBags` (`BagMRU` matrices mapping every folder ever opened), `MountPoints2` (archived external hardware/USB history), and kernel-level program execution signatures.
* **The "Big Three" Forensic Monoliths:** 
  * **AmCache Hive:** The primary forensic repository tracking application installations and historical execution pathways (`Amcache.hve`).
  * **AppCompatCache (Shimcache):** Executive control structure tracking timestamps and execution contexts of every binary loaded by the OS.
  * **Background Activity Monitor (BAM):** Kernel-level service documenting real-time active execution frequencies and system interactions.
* **Filesystem & Snapshot Journals:** Cryptographic purging of the NTFS Change Journal (`$UsnJrnl`), structural filesystem transaction logs (`$LogFile`), transactional resource layers (`$Txf`), and full erasure of system snapshot restoration frames (Volume Shadow Copies / VSS).
* **Volatile Memory & Storage Contexts:** Complete system configuration triggers for Page File Zero-on-Shutdown parameters, full execution disabling/purging of the core Hibernation RAM dump (`hiberfil.sys`), Windows Core Activity Store (`ActivitiesCache.db`), and local hardware device class unique signature identifiers.

---

## Target Audience and Use Cases

* Security Professionals and Penetration Testers: Ideal for clearing digital footprints on authorized machines or evaluating whether forensic logging mechanisms can be successfully neutralized during post-incident recovery assessments.
* System Administrators: Efficiently sanitizes corporate workstations before transitioning hardware between employees, ensuring no residual telemetry, application history, or deep log data remains.
* Advanced Power Users: Tailored for privacy-conscious individuals demanding total authority over their local tracking data with a zero-external-telemetry standalone framework.

---

## Installation and Usage

REDACT operates entirely as a zero-footprint standalone local utility with zero external installation metadata or background phone-home routines.

### Prerequisites
* Windows 11 64-bit
* Administrator privileges Required to access locked registry structures and system logs

### Running the Utility
1. Download the latest compiled executable from the official project page or run the core script natively.
2. Launch the application. 
3. Accept the User Account Control UAC elevation prompt to grant administrative permissions.
4. Select your desired sensitivity tier, toggle parameters, and execute the sanitization matrix.

---

## License and Legal

Distributed under the MIT License. See LICENSE for more information.

Disclaimer: This software is an advanced anti-forensic system modifier. It is designed to safely purge telemetry and system metadata while leaving your core operating system and personal files intact. However, because it alters low-level registry keys and volatile system logs, it should be used at your own discretion. The developers assume no liability for unintended data loss.
