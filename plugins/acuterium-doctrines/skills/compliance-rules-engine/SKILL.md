---
name: compliance-rules-engine
description: "Prometheus-compatible compliance monitoring rules for LLM cost tracking, uptime alerting, and predictive rerouting triggers. Defines recording rules for aggregated cost metrics and alerting rules for uptime degradation. Use when: compliance rules; cost monitoring; uptime alert; rerouting trigger; prometheus; llm cost; uptime threshold; compliance yaml"
---

<!-- Source doctrine: ACU-SKILL-PAN-004 (ACU-PAN-COMPLIANCE-001.md) — Acuterium proprietary. -->

# Compliance Rules Engine

## Rule Groups

### llm_cost_rules

**Recording Rule: `llm_cost_sum`**
Aggregates inference costs across all unified-route LLM providers.
Expression: `sum by (llm_provider) (llm_cost{unified_route="true"})`

**Alert: `LLM_Uptime_Critical`**
Triggers when any LLM provider's predictive uptime score drops below 80%.
- Expression: `llm_uptime < 0.8`
- Duration: 1 minute sustained
- Severity: CRITICAL
- Action: Triggers predictive rerouting via ADOCP to fallback LLM

## Integration with Pan Framework

- **Intelligence Layer**: PerformanceTracker KPI thresholds aligned with these rules
- **Feedback Loop**: Uptime alerts generate `FeedbackType.RESOURCE` entries
- **Swarm Coordinator**: Node health checks reference uptime thresholds
- **Resource Allocator**: Cost metrics inform COST_OPTIMAL strategy weighting

## Golden Schema Alignment

Maps to: `sub_models[].predictive_uptime_score` and `sub_models[].cost`
