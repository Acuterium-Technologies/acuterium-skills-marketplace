---
name: copilot-terraform-azurerm-set-diff-analyzer
description: "Analyze Terraform plan JSON output for AzureRM Provider to distinguish between false-positive diffs (order-only changes in Set-type attributes) and actual resource changes. Use when reviewing terraform plan output for Azure resources like Application Gateway, Load Balancer, Firewall, Front Door, NSG, and other resources with Set-type attributes that cause spurious diffs due to internal ordering changes."
---

<!-- Acuterium registry: wagha | ACU-SKILL-1998 | category=cloud-azure | thread=T13 -->

# Terraform Azurerm Set Diff Analyzer

## Description
Analyze Terraform plan JSON output for AzureRM Provider to distinguish between false-positive diffs (order-only changes in Set-type attributes) and actual resource changes. Use when reviewing terraform plan output for Azure resources like Application Gateway, Load Balancer, Firewall, Front Door, NSG, and other resources with Set-type attributes that cause spurious diffs due to internal ordering changes.

## Acuterium Integration
- **Thread:** T13 — ACAI V2
- **Shard:** Marel
- **Layers:** L5, L6, L7
- **Governance:** restricted
- **Sovereignty Score:** 8/10
- **PSI Minimum:** 10.0

## Source
- **Repository:** github/awesome-copilot
- **File:** skills/terraform-azurerm-set-diff-analyzer/SKILL.md
- **Author:** GitHub Copilot Community
