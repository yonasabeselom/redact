# REDACT v1.0

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