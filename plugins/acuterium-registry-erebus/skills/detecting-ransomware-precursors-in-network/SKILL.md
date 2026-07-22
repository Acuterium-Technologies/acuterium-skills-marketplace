---
name: detecting-ransomware-precursors-in-network
description: "Detects early-stage ransomware indicators in network traffic before encryption begins, including initial access broker activity, command-and-control beaconing, credential harvesting, reconnaissance scanning, and staging behavior. Uses network detection tools (Zeek, Suricata, Arkime), SIEM correlation rules, and threat intelligence feeds to identify ransomware precursor patterns such as Cobalt Strike beacons, Mimikatz network signatures, and RDP brute-force attempts. Activates for requests involving pre-ransomware detection, network-based ransomware indicators, or early warning ransomware monitoring."
---

<!-- Acuterium registry: erebus-cse | ACU-SKILL-1426 | category=malware | thread=T08 -->

# Detecting Ransomware Precursors In Network

## Description
Detects early-stage ransomware indicators in network traffic before encryption begins, including initial access broker activity, command-and-control beaconing, credential harvesting, reconnaissance scanning, and staging behavior. Uses network detection tools (Zeek, Suricata, Arkime), SIEM correlation rules, and threat intelligence feeds to identify ransomware precursor patterns such as Cobalt Strike beacons, Mimikatz network signatures, and RDP brute-force attempts. Activates for requests involving pre-ransomware detection, network-based ransomware indicators, or early warning ransomware monitoring.


## Acuterium Integration
- **Thread:** T08 — ZURD
- **Shard:** Tenebris-ACIWS
- **Layers:** L8, L9, L10
- **Governance:** sovereign
- **Sovereignty Score:** 10/10
- **PSI Minimum:** 10.0

## Source
- **Repository:** mukul975/Anthropic-Cybersecurity-Skills
- **File:** skills/detecting-ransomware-precursors-in-network/SKILL.md
- **Author:** cybersecurity-community
