---
name: performing-api-rate-limiting-bypass
description: "Tests API rate limiting implementations for bypass vulnerabilities by manipulating request headers, IP addresses, HTTP methods, API versions, and encoding schemes to circumvent request throttling controls. The tester identifies rate limit headers, determines enforcement mechanisms, and attempts bypasses including X-Forwarded-For spoofing, parameter pollution, case variation, and endpoint path manipulation. Maps to OWASP API4:2023 Unrestricted Resource Consumption. Activates for requests involving rate limit bypass, API throttling evasion, brute force protection testing, or API abuse prevention assessment."
---

<!-- Acuterium registry: erebus-cse | ACU-SKILL-1638 | category=red-team | thread=T08 -->

# Performing Api Rate Limiting Bypass

## Description
Tests API rate limiting implementations for bypass vulnerabilities by manipulating request headers, IP addresses, HTTP methods, API versions, and encoding schemes to circumvent request throttling controls. The tester identifies rate limit headers, determines enforcement mechanisms, and attempts bypasses including X-Forwarded-For spoofing, parameter pollution, case variation, and endpoint path manipulation. Maps to OWASP API4:2023 Unrestricted Resource Consumption. Activates for requests involving rate limit bypass, API throttling evasion, brute force protection testing, or API abuse prevention assessment.


## Acuterium Integration
- **Thread:** T08 — ZURD
- **Shard:** Tenebris-ACIWS
- **Layers:** L8, L9, L10
- **Governance:** sovereign
- **Sovereignty Score:** 10/10
- **PSI Minimum:** 10.0

## Source
- **Repository:** mukul975/Anthropic-Cybersecurity-Skills
- **File:** skills/performing-api-rate-limiting-bypass/SKILL.md
- **Author:** cybersecurity-community
