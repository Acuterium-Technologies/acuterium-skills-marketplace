---
name: detecting-fileless-attacks-on-endpoints
description: "Detects fileless malware and in-memory attacks that execute entirely in RAM without writing persistent files to disk, evading traditional antivirus. Use when building detections for PowerShell-based attacks, reflective DLL injection, WMI persistence, and registry-resident malware. Activates for requests involving fileless malware detection, in-memory attacks, PowerShell exploitation, or living-off-the-land techniques."
---

<!-- Acuterium registry: erebus-cse | ACU-SKILL-1405 | category=malware | thread=T08 -->

# Detecting Fileless Attacks On Endpoints

## Description
Detects fileless malware and in-memory attacks that execute entirely in RAM without writing persistent files to disk, evading traditional antivirus. Use when building detections for PowerShell-based attacks, reflective DLL injection, WMI persistence, and registry-resident malware. Activates for requests involving fileless malware detection, in-memory attacks, PowerShell exploitation, or living-off-the-land techniques.


## Acuterium Integration
- **Thread:** T08 — ZURD
- **Shard:** Tenebris-ACIWS
- **Layers:** L8, L9, L10
- **Governance:** sovereign
- **Sovereignty Score:** 10/10
- **PSI Minimum:** 10.0

## Source
- **Repository:** mukul975/Anthropic-Cybersecurity-Skills
- **File:** skills/detecting-fileless-attacks-on-endpoints/SKILL.md
- **Author:** cybersecurity-community
