---
name: risk-assessment-intelligence-agent
description: "Sovereign AI agent for comprehensive compliance risk assessment. Analyzes historical data, entity profiles, transactions, and regulatory context to identify compliance risks proactively. Use when: risk assessment; compliance risk; predictive risk; risk scoring; risk matrix; sanctions screening"
---

<!-- Source: ACU-SKILL-COMP-004 — Acuterium compliance-ai, proprietary. -->

# Risk Assessment Intelligence Agent — SKILL.md

## 1. Purpose

Sovereign AI agent for comprehensive compliance risk assessment. Analyzes historical data, entity profiles, transactions, and regulatory context to identify compliance risks proactively. Detects structured transactions designed to evade reporting thresholds, flags sanctioned entities, and predicts emerging risk trends using AI-powered modeling.

## 2. Capabilities

- Analyzes historical data, customer/entity profiles, and transactions for compliance risks
- Detects structured transactions designed to evade reporting thresholds (AML/CFT)
- Flags individuals and entities on sanctions lists across 247 jurisdictions
- Predictive modeling for early detection of emerging risk trends
- Risk matrix generation with severity/likelihood scoring
- Entity risk scoring with consciousness-weighted Compliance Assurance formula
- Integrates with Ūrānā's Legal Entity Intelligence Protocol (LEIP)

## 3. Implementation Architecture

```typescript
interface RiskAssessmentConfig {
  scope: 'entity' | 'transaction' | 'regulatory' | 'operational' | 'comprehensive';
  dataInputs: DataSource[];
  sanctionsLists: string[];
  jurisdictions: string[];
  riskModel: 'statistical' | 'ml_predictive' | 'hybrid';
  thresholds: RiskThresholds;
}

interface EntityRiskProfile {
  entityId: string;
  riskScore: number;             // 0-100
  riskCategory: 'critical' | 'high' | 'medium' | 'low';
  riskFactors: RiskFactor[];
  sanctionsHits: SanctionsMatch[];
  adverseMedia: AdverseMediaHit[];
  pepsScreening: PEPResult[];
  recommendations: string[];
}

async function assessRisk(config: RiskAssessmentConfig): Promise<RiskAssessmentReport> {
  const entityProfiles = await buildEntityProfiles(config.dataInputs);
  const sanctionsScreened = await screenAgainstSanctions(entityProfiles, config.sanctionsLists);
  const transactionPatterns = await analyzeTransactionPatterns(config.dataInputs);
  const predictiveRisks = await runPredictiveModeling(transactionPatterns, config.riskModel);
  const riskMatrix = await generateRiskMatrix(sanctionsScreened, predictiveRisks);
  return { entityProfiles: sanctionsScreened, transactionPatterns, predictiveRisks, riskMatrix };
}
```

## 4. Quality Metrics

| Metric | Target |
|---|---|
| Sanctions screening accuracy | ≥ 99.5% |
| Risk scoring precision | ≥ 93% |
| False positive rate | ≤ 3% |
| Predictive risk detection lead time | ≥ 30 days ahead |
