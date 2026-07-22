---
name: qa-quality-assurance-framework-agent
description: "Sovereign AI agent implementing a proactive, generative AI-enabled quality assurance framework across three functional domains: supplier performance oversight, in-process control, and post-market feedback. Based on the Ilieva et al. Use when: quality assurance; QA framework; process control; defect detection; SPC statistical process control; FMEA"
---

<!-- Source: ACU-SKILL-QA-001 — Acuterium quality-assurance, proprietary. -->

# QA Quality Assurance Framework Agent — SKILL.md

## 1. Purpose

Sovereign AI agent implementing a proactive, generative AI-enabled quality assurance framework across three functional domains: supplier performance oversight, in-process control, and post-market feedback. Based on the Ilieva et al. (2026) conceptual framework with Plan-Execute-Improve cycle integration. Deployed within Ūrānā for institutional quality assurance and accreditation intelligence.

## 2. Domain Mapping

| Dimension | Value |
|---|---|
| **Primary Platform** | Ūrānā — QA & Accreditation Intelligence |
| **Secondary Platform** | RUZN.AI — Government QA Oversight |
| **HISN AL-WUJŪD Shard** | W-07 (Ūrānā-INTEL) |
| **Framework Basis** | Ilieva et al. (2026) — Generative AI-Based Framework for Proactive QA and Auditing |
| **Quality Standards** | ISO 9001, ISO/IEC 42001, IATF 16949, ISO/IEC 17025 |

## 3. Three Functional Domains

### Domain 1: Supplier Performance Oversight
- Automated documentation generation and review for supplier qualifications
- Early risk identification through AI-powered supplier scorecards
- PPAP evidence completeness validation
- Supplier communication automation with intelligent form completion

### Domain 2: In-Process Control
- Real-time anomaly detection with SPC-based triage
- Process Capability Index (Cp/Cpk) monitoring with drift alerts
- AI-augmented FMEA for failure mode identification and action prioritization
- Interactive inspection guidance with context-aware operator support

### Domain 3: Post-Market Feedback
- Predictive analytics for warranty clustering and complaint patterns
- Prioritized CAPA (Corrective and Preventive Action) preparation
- Customer feedback classification and sentiment analysis
- Post-market surveillance with regulatory reporting automation

## 4. Implementation Architecture

```typescript
interface QAFrameworkConfig {
  domains: ('supplier' | 'in_process' | 'post_market')[];
  qualityStandards: string[];    // ISO 9001, ISO/IEC 42001, etc.
  spcParameters: SPCConfig;
  fmeaTemplates: string[];
  capaWorkflow: CAPAConfig;
  humanInTheLoop: HumanCheckpoint[];
}

interface SPCConfig {
  controlLimits: { upper: number; lower: number };
  capabilityTargets: { cp: number; cpk: number };
  samplingFrequency: string;
  alertThresholds: number[];
}

interface CAPARecord {
  capaId: string;
  rootCause: string;
  containmentActions: Action[];
  correctionActions: Action[];
  preventiveActions: Action[];
  verificationResults: VerificationResult[];
  closureCriteria: string;
  auditTrail: AuditEntry[];
}

// Plan-Execute-Improve cycle
async function runQACycle(config: QAFrameworkConfig): Promise<QACycleReport> {
  // PLAN
  const riskAssessment = await assessSupplierRisks(config);
  const controlPlan = await generateControlPlan(riskAssessment, config.qualityStandards);
  
  // EXECUTE
  const spcResults = await monitorProcesses(config.spcParameters);
  const anomalies = await detectAnomalies(spcResults);
  const inspectionResults = await conductInspections(anomalies);
  
  // IMPROVE
  const capas = await generateCAPAs(inspectionResults);
  const postMarketAnalysis = await analyzePostMarketFeedback();
  const improvements = await recommendImprovements(capas, postMarketAnalysis);
  
  return compileQAReport(controlPlan, spcResults, capas, improvements);
}
```

## 5. Key Quality Metrics (per Ilieva et al.)

| Metric | Description |
|---|---|
| First Pass Yield (FPY) | % products manufactured correctly without rework |
| Defects Per Million Opportunities (DPMO) | Normalized defect rate |
| Process Capability (Cp/Cpk) | How well process meets specification limits |
| Overall Equipment Effectiveness (OEE) | Availability × Performance × Quality |
| Cost of Poor Quality (CoPQ) | Costs from scrap, rework, and warranty claims |

## 6. Trigger Keywords

```
quality assurance, QA framework, process control, defect detection,
SPC, statistical process control, FMEA, CAPA, corrective action,
supplier quality, in-process control, post-market surveillance,
ISO 9001, quality management system, Six Sigma, DMAIC,
ضمان الجودة, إطار الجودة, التحكم في العمليات, اكتشاف العيوب
```

## 7. References

- Ilieva et al. (2026): A Generative AI-Based Framework for Proactive QA and Auditing
- ISO 9001:2015, ISO/IEC 42001:2023, IATF 16949
- NIST AI Risk Management Framework
