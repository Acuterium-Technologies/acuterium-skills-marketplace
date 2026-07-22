---
name: detecting-dcsync-attack-in-active-directory
description: "Detect DCSync attacks where adversaries abuse Active Directory replication privileges to extract password hashes by monitoring for non-domain-controller accounts requesting directory replication via DsGetNCChanges."
---

<!-- Acuterium registry: erebus-cse | ACU-SKILL-1399 | category=security | thread=T08 -->

# Detecting Dcsync Attack In Active Directory

## Description
Detect DCSync attacks where adversaries abuse Active Directory replication privileges to extract password hashes by monitoring for non-domain-controller accounts requesting directory replication via DsGetNCChanges.

## Acuterium Integration
- **Thread:** T08 — ZURD
- **Shard:** Tenebris-ACIWS
- **Layers:** L8, L9, L10
- **Governance:** sovereign
- **Sovereignty Score:** 10/10
- **PSI Minimum:** 10.0

## Source
- **Repository:** mukul975/Anthropic-Cybersecurity-Skills
- **File:** skills/detecting-dcsync-attack-in-active-directory/SKILL.md
- **Author:** cybersecurity-community
