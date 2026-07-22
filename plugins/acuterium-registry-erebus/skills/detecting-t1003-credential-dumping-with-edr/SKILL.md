---
name: detecting-t1003-credential-dumping-with-edr
description: "Detect OS credential dumping techniques targeting LSASS memory, SAM database, NTDS.dit, and cached credentials using EDR telemetry, Sysmon process access monitoring, and Windows security event correlation."
---

<!-- Acuterium registry: erebus-cse | ACU-SKILL-1434 | category=security | thread=T08 -->

# Detecting T1003 Credential Dumping With Edr

## Description
Detect OS credential dumping techniques targeting LSASS memory, SAM database, NTDS.dit, and cached credentials using EDR telemetry, Sysmon process access monitoring, and Windows security event correlation.

## Acuterium Integration
- **Thread:** T08 — ZURD
- **Shard:** Tenebris-ACIWS
- **Layers:** L8, L9, L10
- **Governance:** sovereign
- **Sovereignty Score:** 10/10
- **PSI Minimum:** 10.0

## Source
- **Repository:** mukul975/Anthropic-Cybersecurity-Skills
- **File:** skills/detecting-t1003-credential-dumping-with-edr/SKILL.md
- **Author:** cybersecurity-community
