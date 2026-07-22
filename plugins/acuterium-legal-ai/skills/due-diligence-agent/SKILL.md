---
name: due-diligence-agent
description: "Sovereign AI agent for automated due diligence across M&A, government procurement, sovereign wealth fund investments, and institutional integrity assessments. Processes large document repositories to identify risks, inconsistencies, and missing information with immutable evidence chains. Use when: due diligence; data room analysis; M&A review; risk identification; document categorization"
---

<!-- Source: ACU-SKILL-LEG-004 — Acuterium legal-ai, proprietary. -->

# Due Diligence Agent — SKILL.md

## 1. Purpose

Sovereign AI agent for automated due diligence across M&A, government procurement, sovereign wealth fund investments, and institutional integrity assessments. Processes large document repositories to identify risks, inconsistencies, and missing information with immutable evidence chains.

## 2. Domain Mapping

| Dimension | Value |
|---|---|
| **Primary Platform** | RUZN.AI + Ūrānā (dual deployment) |
| **HISN AL-WUJŪD Shards** | C-01 (RUZN-GOV) + W-07 (Ūrānā-INTEL) |
| **Sovereignty Tier** | 10/10 — Air-gap, zero cloud |

## 3. Capabilities

- Analyzes entire data rooms (10,000+ documents) automatically with progressive disclosure
- Categorizes documents by type, relevance, and risk tier
- Identifies red flags: undisclosed liabilities, regulatory violations, beneficial ownership gaps
- Cross-references information across documents for consistency verification
- Generates structured due diligence reports with risk heatmaps
- Entity relationship mapping across 247 jurisdictions (LEIP protocol integration)
- Beneficial ownership identification with UBO chain tracing
- Immutable evidence locker with blockchain-verified timestamping

## 4. Implementation Architecture

```typescript
interface DueDiligenceConfig {
  scope: 'full' | 'financial' | 'legal' | 'regulatory' | 'integrity';
  dataRoomPath: string;
  jurisdictions: string[];
  entityFocus: string[];
  riskFramework: 'standard' | 'enhanced' | 'sovereign_integrity';
  outputFormat: 'executive_summary' | 'detailed_report' | 'risk_heatmap';
}

interface DDFinding {
  finding_id: string;
  category: 'red_flag' | 'amber_flag' | 'information_gap' | 'inconsistency';
  severity: 'critical' | 'high' | 'medium' | 'low';
  description: string;
  evidence_refs: string[];
  recommendation: string;
  legal_basis: string;
}

async function conductDueDiligence(config: DueDiligenceConfig): Promise<DDReport> {
  const documents = await ingestDataRoom(config.dataRoomPath);
  const classified = await classifyDocuments(documents);
  const entityMap = await buildEntityRelationshipMap(classified, config.jurisdictions);
  const findings = await analyzeForRisks(classified, entityMap, config.riskFramework);
  const crossRef = await crossReferenceFindings(findings, classified);
  const report = await generateDDReport(crossRef, config.outputFormat);
  await lockEvidence(report, 'due-diligence-evidence-locker');
  return report;
}
```

## 5. Trigger Keywords

```
due diligence, data room, M&A review, risk identification, document categorization,
beneficial ownership, entity mapping, UBO tracing, red flag detection,
integrity assessment, government procurement review, sovereign wealth due diligence,
العناية الواجبة, تحليل غرفة البيانات, تحديد المخاطر, ملكية فعلية, تقييم النزاهة
```

## 6. Quality Metrics

| Metric | Target |
|---|---|
| Document classification accuracy | ≥ 96% |
| Red flag detection rate | ≥ 94% |
| Cross-reference consistency check | ≥ 98% |
| Data room processing time (10K docs) | ≤ 4 hours |
| False positive rate | ≤ 3% |
