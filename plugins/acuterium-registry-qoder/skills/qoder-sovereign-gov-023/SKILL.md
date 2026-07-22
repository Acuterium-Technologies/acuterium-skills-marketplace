---
name: qoder-sovereign-gov-023
description: "| Layer | Enum Values | Purpose | |-------|-------------|---------| | ACT (Action) | REQUIRED / ELEVATED / UNRESTRICTED | Permission to mutate state | | INT (Integrity) | REQUIRED / ELEVATED / UNRESTRICTED | Data integrity verification | | CON (Consent) | OPTIONAL / REQUIRED | Human-in-the-loop mandate |"
---

<!-- Acuterium registry: qoder |  | category= | thread= -->

# Sovereignty Governance Layer

## ASIP v2 — 7-Stage Soul Infusion Pipeline
1. Identity injection (doctrine, tone, ethics, sovereign behavior)
2. Sovereignty validation (tier check, base model admissibility)
3. Governance tier assignment (determine product tier 3-10)
4. TokenBridge authorization (ACT/INT/CON permission check)
5. Protocol binding (wire governance into system surfaces)
6. Behavioral constraints (enforce red lines, anti-escalation)
7. Output formatting (classification headers, provenance metadata)

## TokenBridge Authorization

| Layer | Enum Values | Purpose |
|-------|-------------|---------|
| ACT (Action) | REQUIRED / ELEVATED / UNRESTRICTED | Permission to mutate state |
| INT (Integrity) | REQUIRED / ELEVATED / UNRESTRICTED | Data integrity verification |
| CON (Consent) | OPTIONAL / REQUIRED | Human-in-the-loop mandate |

Read-only skills: ACT=REQUIRED, INT=REQUIRED, CON=OPTIONAL
Destructive skills: ACT=ELEVATED, CON=REQUIRED

## CWH Attestation (distinct from TokenBridge)
- HITL mandate-attestation patterns
- Signed provenance for datasets, runs, checkpoints, evaluations
- Supply-chain attestation style
- CWH ≠ TokenBridge: authorization grants access, attestation proves origin

## M-PCB Doctrine
Core rule: Algorithms are NOT disclosed — only outputs are shared. External parties see results, never methodology.

## APMS Protocol Management
- 523 protocols with FTS5 full-text search
- QA guardrails on every protocol operation
- Lifecycle: DRAFT → REVIEW → PUBLISHED → DEPLOYED
- Schema version: acu-json-v1

## 5 Owned Control Domains
1. MAPL_POLICY — machine-readable allow/deny logic, constraint evaluation
2. ASIP_IDENTITY_GATING — doctrine, tone, ethics infusion into all surfaces
3. CWH_ATTESTATION — signed provenance chain
4. ACUTECT_CODEX_ENFORCEMENT — code security standards enforcement
5. APMS_PROVENANCE_AND_REGISTRY — protocol lifecycle and audit trail

## Governance Packet Schema
```yaml
policy_governance_packet:
  request_class: MAPL_POLICY | ASIP_IDENTITY_GATING | CWH_ATTESTATION | ACUTECT_CODEX_ENFORCEMENT | APMS_PROVENANCE | MIXED
  constitutional_basis: { doctrine_rules[], residency_requirements[], red_lines[] }
  governance_artifacts: [{ artifact_id, artifact_type, status: BUILT|PARTIAL|DESIGNED|ASPIRATIONAL|PROHIBITED }]
  enforcement_bindings: [{ surface, mechanism, blocking: bool }]
  sovereignty_checks: { base_model_admissibility, residency_status, privilege_escalation_risk, silent_bypass_risk }
  downstream_handoffs: [{ target_skill, reason }]
```

## 8 Absolute Prohibitions (NEVER)
1. Never admit capability that cannot be expressed and audited as policy
2. Never replace explicit policy with vague prompt-only instructions
3. Never treat TokenBridge authorization as equivalent to attestation provenance
4. Never weaken universal red lines into optional warnings
5. Never permit prohibited base-model contamination
6. Never create hidden privilege-escalation paths
7. Never silently bypass residency, provenance, or identity requirements
8. Never drift into writing training engines or deployment actions

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY | **Shard:** W-09 Baranurion
- **TokenBridge:** ACT=REQUIRED, INT=REQUIRED, CON=OPTIONAL
- **Sovereignty Score:** 1010 | **Data Residency:** OMAN
