---
name: compliance-workflow-automation-agent
description: "Sovereign AI agent for orchestrating end-to-end compliance workflows including customer due diligence (CDD), KYC verification, fraud screening, document generation, case routing, and exception escalation. Sequences and prioritizes activities automatically while maintaining human-in-the-loop checkpoints for critical decisions. Use when: compliance workflow; due diligence automation; KYC automation; fraud screening; workflow orchestration"
---

<!-- Source: ACU-SKILL-COMP-005 — Acuterium compliance-ai, proprietary. -->

# Compliance Workflow Automation Agent — SKILL.md

## 1. Purpose

Sovereign AI agent for orchestrating end-to-end compliance workflows including customer due diligence (CDD), KYC verification, fraud screening, document generation, case routing, and exception escalation. Sequences and prioritizes activities automatically while maintaining human-in-the-loop checkpoints for critical decisions.

## 2. Capabilities

- Automates customer due diligence and KYC workflows end-to-end
- Fraud screening against transaction patterns and behavioral analytics
- Document generation for compliance filings and regulatory submissions
- Intelligent case routing and priority queuing based on risk scores
- Exception escalation with automatic context packaging
- Multi-agent coordination: screening agent → review agent → approval agent
- Supports Omani AML/CFT requirements and CBO regulatory mandates

## 3. Implementation Architecture

```typescript
interface ComplianceWorkflow {
  workflowType: 'KYC' | 'CDD' | 'EDD' | 'SAR' | 'STR' | 'fraud_screening';
  subject: EntitySubject;
  dataInputs: DataSource[];
  riskLevel: 'standard' | 'enhanced' | 'simplified';
  approvalChain: Approver[];
  slaMinutes: number;
}

async function executeComplianceWorkflow(workflow: ComplianceWorkflow): Promise<WorkflowResult> {
  const screened = await runScreeningAgent(workflow.subject, workflow.dataInputs);
  const reviewed = await runReviewAgent(screened, workflow.riskLevel);
  if (reviewed.requiresEscalation) {
    await escalateToHuman(reviewed, workflow.approvalChain);
  }
  const decision = await obtainDecision(reviewed);
  const documentation = await generateComplianceDocumentation(decision, workflow.workflowType);
  await archiveWorkflow(documentation);
  return { decision, documentation, processingTime: calculateSLA(workflow) };
}
```

## 4. Quality Metrics

| Metric | Target |
|---|---|
| Workflow completion rate | ≥ 98% |
| SLA adherence | ≥ 95% |
| Screening accuracy | ≥ 96% |
| Exception routing accuracy | ≥ 99% |
