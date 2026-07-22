---
name: vuln-triage
description: "Triage vulnerability scan results by cross-referencing CVEs against asset criticality, EPSS scores, CISA KEV status, and known public exploits. Produces a prioritized remediation list with org-defined risk buckets and creates Jira tickets for critical/high findings. Trigger when user uploads scan exports (.csv, .json, .nessus, .xml), mentions 'vuln triage', 'CVE prioritization', 'scan results', 'vulnerability report', 'prioritize findings', or 'what should we patch first'. Also trigger when user pastes raw CVE lists or asks about exploitability of specific CVEs."
---

<!-- Acuterium registry: erebus-cse | ACU-SKILL-2136 | category=pentesting | thread=T08 -->

# Vuln Triage

## Description
Triage vulnerability scan results by cross-referencing CVEs against asset criticality, EPSS scores, CISA KEV status, and known public exploits. Produces a prioritized remediation list with org-defined risk buckets and creates Jira tickets for critical/high findings. Trigger when user uploads scan exports (.csv, .json, .nessus, .xml), mentions "vuln triage", "CVE prioritization", "scan results", "vulnerability report", "prioritize findings", or "what should we patch first". Also trigger when user pastes raw CVE lists or asks about exploitability of specific CVEs.


## Acuterium Integration
- **Thread:** T08 — ZURD
- **Shard:** Tenebris-ACIWS
- **Layers:** L8, L9, L10
- **Governance:** sovereign
- **Sovereignty Score:** 10/10
- **PSI Minimum:** 10.0

## Source
- **Repository:** Poatan222/Skills-security
- **File:** vuln-triage/SKILL.md
- **Author:** Poatan222/Skills-security
