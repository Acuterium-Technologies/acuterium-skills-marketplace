---
name: audit-trail-evidence-management-agent
description: "Sovereign AI agent for automatic generation, maintenance, and verification of audit trails across all Acuterium compliance and legal platforms. Implements Ūrānā's Evidence Locker with immutable blockchain-verified timestamping and chain of custody tracking. Use when: audit trail; evidence management; evidence locker; blockchain timestamp; chain of custody; immutable records"
---

<!-- Source: ACU-SKILL-AUD-003 — Acuterium audit-ai, proprietary. -->

# Audit Trail & Evidence Management Agent — SKILL.md

## 1. Purpose

Sovereign AI agent for automatic generation, maintenance, and verification of audit trails across all Acuterium compliance and legal platforms. Implements Ūrānā's Evidence Locker with immutable blockchain-verified timestamping and chain of custody tracking. Ensures every compliance decision, review action, and status change is recorded with full provenance.

## 2. Capabilities

- Automatically generates and maintains structured audit logs of all compliance-related actions
- Every decision or output recorded with timestamp, actor, context, and evidence chain
- Blockchain-verified timestamping prevents evidence tampering or "New Evidence" rejection
- Comprehensive chain of custody tracking for litigation and regulatory submissions
- Structured documentation facilitating regulatory reporting (XBRL, iXBRL)
- Evidence quality scoring per compliance assurance formula (E_evidence-quality)
- Cross-platform evidence aggregation from RUZN, Ūrānā, Erebus-CSE

## 3. Implementation Architecture

```typescript
interface EvidenceRecord {
  record_id: string;
  source_platform: 'ruzn' | 'urana' | 'erebus';
  action_type: string;
  actor: string;
  timestamp: string;           // ISO 8601
  blockchain_hash: string;
  evidence_payload: any;
  chain_of_custody: CustodyEntry[];
  quality_score: number;       // 0-1
  retention_policy: string;
}

interface CustodyEntry {
  custodian: string;
  action: 'created' | 'accessed' | 'transferred' | 'sealed' | 'submitted';
  timestamp: string;
  verification_hash: string;
}

async function recordAuditTrail(action: AuditAction): Promise<EvidenceRecord> {
  const record = createEvidenceRecord(action);
  const hash = await computeBlockchainHash(record);
  record.blockchain_hash = hash;
  await storeInEvidenceLocker(record);
  await updateChainOfCustody(record, 'created');
  return record;
}
```

## 4. Quality Metrics

| Metric | Target |
|---|---|
| Evidence immutability | 100% (blockchain-verified) |
| Audit trail completeness | ≥ 99.9% |
| Retrieval time | ≤ 200ms |
| Reporting accuracy (XBRL) | ≥ 98.3% |
