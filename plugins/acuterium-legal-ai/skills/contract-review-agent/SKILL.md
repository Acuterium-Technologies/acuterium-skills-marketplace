---
name: contract-review-agent
description: "Sovereign-grade AI agent for automated contract review, clause extraction, risk flagging, and compliance verification against Omani/GCC legal standards. Designed for deployment within RUZN.AI's Government Edition and Ūrānā's regulatory intelligence layer. Use when: contract review; agreement analysis; clause detection; unfavorable terms; contract compliance"
---

<!-- Source: ACU-SKILL-LEG-001 — Acuterium legal-ai, proprietary. -->

# Contract Review Agent — SKILL.md

## 1. Purpose

Sovereign-grade AI agent for automated contract review, clause extraction, risk flagging, and compliance verification against Omani/GCC legal standards. Designed for deployment within RUZN.AI's Government Edition and Ūrānā's regulatory intelligence layer.

## 2. Domain Mapping

| Dimension | Value |
|---|---|
| **Primary Platform** | RUZN.AI — Sovereign Legal Intelligence |
| **Secondary Platform** | Ūrānā — Defense/Regulatory Intelligence |
| **HISN AL-WUJŪD Shard** | C-01 (RUZN-GOV) |
| **DIARAN-MOE Expert Cluster** | Legal-NLP-001 through Legal-NLP-012 |
| **Sovereignty Tier** | 10/10 — Air-gap capable, zero cloud at runtime |
| **Arabic NLP Engine** | Qwen-2.5 (non-negotiable standard) |
| **Reasoning Engine** | DeepSeek-R1 (air-gap sovereign) |

## 3. Capabilities

- Scans agreements to identify missing, problematic, or non-standard clauses
- Compares contracts against organizational template libraries and Omani/GCC statutory requirements
- Detects inconsistent definitions across sections and cross-references
- Flags unfavorable liability, indemnity, and termination terms
- Generates structured review summaries with risk-scored recommendations
- Supports bilingual Arabic/English contract corpus with RTL-native rendering
- Produces immutable audit trails for every review action

## 4. Implementation Architecture

```typescript
interface ContractReviewConfig {
  jurisdiction: 'OM' | 'GCC' | 'INTERNATIONAL';
  templateLibrary: string; // path to sovereign template store
  riskThresholds: {
    liability: number;    // 0-1 tolerance
    indemnity: number;
    termination: number;
    ip_assignment: number;
  };
  outputFormat: 'structured_json' | 'docx_report' | 'ruzn_dashboard';
  language: 'ar' | 'en' | 'bilingual';
}

interface ClauseAnalysis {
  clause_id: string;
  clause_type: string;
  risk_score: number;        // 0-100
  deviation_from_template: number; // percentage
  recommendation: string;
  legal_citation: string;    // Omani Royal Decree / GCC statute
  confidence: number;
}

// Core review pipeline
async function reviewContract(
  document: Buffer,
  config: ContractReviewConfig
): Promise<ContractReviewReport> {
  const extracted = await extractClauses(document, config.language);
  const compared = await compareToTemplates(extracted, config.templateLibrary);
  const riskScored = await assessRisk(compared, config.riskThresholds);
  const report = await generateReport(riskScored, config.outputFormat);
  await createAuditTrail(report, 'contract-review');
  return report;
}
```

## 5. Trigger Keywords (for DIARAN-MOE Routing)

```
contract review, agreement analysis, clause detection, clause extraction,
unfavorable terms, contract compliance, template comparison, liability check,
indemnity review, termination clause, IP assignment, cross-reference check,
مراجعة العقود, تحليل الاتفاقيات, استخراج البنود, شروط المسؤولية,
تحقق من الامتثال, مقارنة النماذج
```

## 6. Sovereignty Rules

1. All contract data processed on sovereign infrastructure — zero cloud SaaS
2. Document corpus never leaves the deployment environment
3. Template libraries stored in HISN AL-WUJŪD encrypted vault
4. Audit trails are immutable and blockchain-timestamped (Ūrānā Evidence Locker)
5. Arabic NLP exclusively via Qwen-2.5 — no third-party API calls
6. Human-in-the-loop mandatory for all final review approvals

## 7. Integration Points

- **RUZN.AI Dashboard**: Review results rendered in Government Edition dark theme
- **Ūrānā Pre-Crime Audit**: Feeds contract risk scores into predictive litigation scoring
- **Erebus-CSE**: Contract metadata scanned for data sovereignty compliance
- **ACAI V2**: Contract review accessible via NEXUS cognitive mode

## 8. Quality Metrics

| Metric | Target |
|---|---|
| Clause extraction accuracy | ≥ 95% |
| Risk scoring precision | ≥ 92% |
| Template deviation detection | ≥ 97% |
| Review time reduction | ≥ 85% vs manual |
| False positive rate | ≤ 5% |

## 9. References

- MindStudio: AI Agents for Legal Professionals (2026)
- Acuterium RUZN Protocol Detailed Specs — Legal Entity Intelligence Protocol (LEIP)
- Royal Decree 111/2011 — State Audit Law (Oman)
- Royal Decree 112/2011 — Protection of Public Funds Law (Oman)
