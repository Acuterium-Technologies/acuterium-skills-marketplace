---
name: policy-enforcement-agent
description: "Sovereign AI agent for monitoring internal activity against organizational policies and regulatory mandates. Detects policy violations in real-time, identifies outdated or conflicting policies through gap analysis, and tracks mandatory training and certification compliance across government and institutional entities. Use when: policy enforcement; policy violation detection; internal policy monitoring; gap analysis"
---

<!-- Source: ACU-SKILL-COMP-003 — Acuterium compliance-ai, proprietary. -->

# Policy Enforcement Agent — SKILL.md

## 1. Purpose

Sovereign AI agent for monitoring internal activity against organizational policies and regulatory mandates. Detects policy violations in real-time, identifies outdated or conflicting policies through gap analysis, and tracks mandatory training and certification compliance across government and institutional entities.

## 2. Capabilities

- Monitors internal communications for sensitive information handling violations
- Tracks completion of mandatory training, certifications, and attestations
- Identifies outdated or conflicting policies through automated gap analysis
- Flags violations early for consistent enforcement across the enterprise
- Generates policy compliance dashboards with risk scoring
- Supports annual financial disclosure duty tracking (Royal Decree 112/2011, Article 12)
- Monitors prohibitions: private sector work, shareholding in connected companies, abuse of position

## 3. Implementation Architecture

```typescript
interface PolicyEnforcementConfig {
  policies: OrganizationalPolicy[];
  monitoredChannels: ('email' | 'documents' | 'access_logs' | 'financial_systems')[];
  violationThresholds: Map<string, number>;
  escalationWorkflow: EscalationLevel[];
}

async function enforcePolicy(config: PolicyEnforcementConfig): Promise<PolicyReport> {
  const activity = await monitorChannels(config.monitoredChannels);
  const violations = await detectViolations(activity, config.policies);
  const gapAnalysis = await analyzeForPolicyGaps(config.policies);
  const trainingStatus = await checkMandatoryTraining(config.policies);
  await escalateViolations(violations, config.escalationWorkflow);
  return { violations, gapAnalysis, trainingStatus, riskScore: computeRiskScore(violations) };
}
```

## 4. Quality Metrics

| Metric | Target |
|---|---|
| Policy violation detection rate | ≥ 93% |
| Gap analysis coverage | ≥ 98% |
| False positive rate | ≤ 5% |
| Training compliance tracking accuracy | ≥ 99% |
