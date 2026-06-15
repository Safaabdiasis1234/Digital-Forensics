
# Portfolio 3 — Forensic Analysis of an Attack

## Overview

This portfolio presents a full forensic investigation of a Windows 10 virtual machine suspected of being used in an insider attack. The investigation focused on identifying malicious activity through Windows Registry analysis, file system examination, and memory forensics.

The image analysed was `win10_Portfolio3-disk.vhd`, and the investigation was conducted using tools including Autopsy, Registry Explorer, and Volatility, in line with ACPO best practice guidelines.

---

## Key Findings

The user account **Student** was identified as the primary actor. On **22nd March 2024**, the following suspicious activity was confirmed:

- Execution of `ART-attack.ps1` — a PowerShell script that automatically installed the Atomic Red Team framework and simulated multiple cyberattack stages
- Creation of a new admin account (`art-test`) at 19:47:49 CET
- Execution of `AdFind.exe`, a known Active Directory enumeration tool
- 11 executable files, 148 DLL files, and 11 batch files created on the same day
- Evidence of process injection, persistence via Run keys and StartUp folder, and privilege escalation
- System shutdown at 19:16:42 UTC, shortly after the suspicious activity

---

## Tools Used

- **Autopsy** — Primary forensic image analysis
- **Registry Explorer** (Eric Zimmerman) — Windows Registry hive analysis
- **Volatility** — Memory forensics (Wow Factor component)
- **PowerShell** — Timestamp conversion and data analysis

---

## Structure

- `portfolio_3_digital_forensics.pdf` — Full investigation report including all 29 questions, Wow Factor analysis, and Executive Summary

---

## Module Info

- **Module:** Digital Forensics — CMP020N210S
- **Assessment:** Coursework Portfolio 3 — Forensic Analysis of an Attack (25% of module)
- **Institution:** University of Roehampton

---

## Disclaimer

This investigation was conducted in a controlled academic environment. All findings are for educational purposes only.
