---
name: internal-audit-automation-agent
description: "Sovereign AI agent for end-to-end internal audit automation. Implements a multi-agent architecture (Data Analyst → Senior Auditor → Audit Manager) for controls testing, risk assessment, fieldwork execution, and audit report generation. Use when: internal audit; controls testing; audit fieldwork; ghost employee detection; audit planning; audit report generation"
---

<!-- Source: ACU-SKILL-AUD-001 — Acuterium audit-ai, proprietary. -->

# Internal Audit Automation Agent — SKILL.md

## 1. Purpose

Sovereign AI agent for end-to-end internal audit automation. Implements a multi-agent architecture (Data Analyst → Senior Auditor → Audit Manager) for controls testing, risk assessment, fieldwork execution, and audit report generation. Derived from AuditBoard best practices and adapted for GCC sovereign deployment.

## 2. Domain Mapping

| Dimension | Value |
|---|---|
| **Primary Platform** | RUZN.AI — Government Audit Intelligence |
| **Secondary Platform** | Ūrānā — Institutional Integrity Assessment |
| **HISN AL-WUJŪD Shards** | C-01, W-07 |
| **Protocol** | Compliance Assurance Protocol (EREBUS-CSE-3A12d-006) |
| **Sovereignty Tier** | 10/10 |

## 3. Multi-Agent Architecture

### Agent 1: Data Analyst Agent
- Retrieves and cleans data from payroll, HR, financial, and operational systems
- Identifies mismatches, anomalies, and statistical outliers
- Produces structured datasets for senior review

### Agent 2: Senior Auditor Agent
- Reviews initial findings and assesses risk levels
- Applies professional judgment heuristics (calibrated from audit standards)
- Prioritizes findings by materiality and control impact

### Agent 3: Audit Manager Agent
- Compiles structured audit reports with executive summaries
- Generates key findings, root cause analysis, and recommendations
- Ensures report adherence to IIA standards and sovereign audit protocols

## 4. Capabilities

- Controls testing: Automated testing against 847 control objectives
- Ghost employee detection: Cross-references termination dates with payroll records
- Expense monitoring: Flags suspicious transactions by pattern and threshold analysis
- Completeness/accuracy testing: Validates population integrity against source SQL
- Audit planning: Analyzes prior audit data, assesses risk, recommends engagement timelines
- Audit report drafting: Structured findings → executive summary → recommendations
- Continuous monitoring shift: From reactive auditing to proactive risk monitoring

## 5. Implementation Architecture

```typescript
interface AuditEngagement {
  engagementId: string;
  scope: 'financial' | 'operational' | 'compliance' | 'IT' | 'integrity';
  entityUnderAudit: string;
  period: { from: string; to: string };
  controlObjectives: string[];
  dataSources: DataSource[];
  riskLevel: 'high' | 'medium' | 'low';
}

interface AuditFinding {
  finding_id: string;
  condition: string;
  criteria: string;
  cause: string;
  effect: string;
  recommendation: string;
  managementResponse?: string;
  riskRating: 'critical' | 'high' | 'medium' | 'low';
  evidenceRefs: string[];
}

// Multi-agent pipeline
async function executeAudit(engagement: AuditEngagement): Promise<AuditReport> {
  // Phase 1: Data Analyst Agent
  const rawData = await dataAnalystAgent.retrieveAndClean(engagement.dataSources);
  const anomalies = await dataAnalystAgent.identifyAnomalies(rawData, engagement.controlObjectives);
  
  // Phase 2: Senior Auditor Agent
  const assessedFindings = await seniorAuditorAgent.assessRisk(anomalies);
  const prioritized = await seniorAuditorAgent.prioritizeByMateriality(assessedFindings);
  
  // Phase 3: Audit Manager Agent
  const report = await auditManagerAgent.compileReport(prioritized, engagement);
  await auditManagerAgent.generateExecutiveSummary(report);
  await lockAuditEvidence(report);
  
  return report;
}
```

## 6. Trigger Keywords

```
internal audit, controls testing, audit fieldwork, ghost employee detection,
expense monitoring, audit planning, audit report, risk assessment,
continuous monitoring, control objectives, audit findings, IIA standards,
completeness accuracy testing, population validation,
تدقيق داخلي, اختبار الضوابط, تخطيط التدقيق, تقرير التدقيق, تقييم المخاطر
```

## 7. Quality Metrics

| Metric | Target |
|---|---|
| Control testing accuracy | ≥ 96.4% |
| Audit finding prevention rate | ≥ 94.8% |
| Manual testing reduction | ≥ 84.7% |
| Audit prep time reduction | ≥ 67.2% |
| Report generation time | ≤ 30 minutes |

## 8. References

- AuditBoard: How AI Agents Will Transform Internal Audit and Compliance (2025)
- Acuterium RUZN Protocol — Compliance Assurance Protocol (EREBUS-CSE-3A12d-006)
- IIA International Standards for Professional Practice of Internal Auditing
