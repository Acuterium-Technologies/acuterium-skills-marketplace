---
name: QODER-HANDOFF-PROTOCOL-024
description: "Acuterium handoff protocol discipline — 18-field handoff packet schema, 7-item downstream acceptance checklist, rejection format with reason codes, 4 mutation classes (0=Read-only, 1=Bounded Artifact, 2=Code Mutation, 3=Deployment), confidence discipline (HIGH/MEDIUM/LOW), staleness rules (6 triggers), 5 upstream-to-downstream patterns, 6-question skill selection decision tree. Use when coordinating multi-agent workflows, enforcing evidence-before-action, or managing session orchestration. Thread 13 — ACAI V2."
---

# Handoff Protocol & Session Orchestration Discipline

## Core Principle
"A handoff is not a courtesy note. It is a control boundary."

## Handoff Packet Schema (18 fields)
```yaml
handoff_packet:
  handoff_version: "1.0"
  produced_by: "<skill-name>"
  handoff_timestamp: "<ISO-8601>"
  mission_id: "<string>"
  task_summary: "<short description>"
  objective_status: CLEAR | PARTIAL | UNCLEAR
  source_of_truth_status: CONFIRMED | PARTIAL | CONFLICTED | UNKNOWN
  repo_truth_status: CONFIRMED | PARTIAL | NOT_APPLICABLE | UNKNOWN
  evidence_status: SUFFICIENT | PARTIAL | INSUFFICIENT | UNKNOWN
  mutation_authority: APPROVED | NOT_APPROVED | NOT_REQUIRED | UNKNOWN
  dominant_risk: "<string>"
  blockers: ["<blocker>"]
  required_next_skill: "<skill-name>"
  recommended_next_action: "<instruction>"
  canonical_sources: [{ path, role: PRIMARY|SECONDARY|REFERENCE }]
  exact_artifacts_reviewed: ["<path>"]
  unresolved_questions: ["<question>"]
  constraints: ["<constraint>"]
  anti_scope: ["<what must not be done>"]
```

## 7-Item Downstream Acceptance Checklist
1. Objective is clear enough to act
2. Canonical source is confirmed
3. Repo truth is confirmed or not applicable
4. Evidence is sufficient
5. Mutation authority is approved or not required
6. Unresolved questions do not affect implementation safety
7. Anti-scope boundaries are explicit

If ANY item fails → reject and route back upstream.

## Mutation Classes

| Class | Description | Approval |
|-------|-------------|----------|
| 0 | Read-only discovery | None required |
| 1 | Bounded artifact generation (specs, schemas, scaffolds) | Self-approved when scope clear |
| 2 | Code or infrastructure mutation | Repo truth confirmed + evidence sufficient + authority approved |
| 3 | Deployment or production-impacting | Explicit approval + downstream gate confirmation |

## Confidence Discipline
Every packet includes: HIGH / MEDIUM / LOW confidence.
If LOW → downstream mutation blocked by default unless explicit override.

## Staleness Rules (6 triggers that invalidate a packet)
1. Repo head or branch changes materially
2. Primary source-of-truth document changes
3. Upload set changes materially
4. Implementation target changes
5. User changes mission scope
6. Approval boundaries change

If stale → must regenerate or revalidate before mutation.

## 6-Question Skill Selection Decision Tree
1. About doctrine/governance? → Constitutional/governance skill
2. About session structure/phasing? → Session orchestration governor
3. Uncertain what exists in repo? → Repo truth mapper
4. Uncertain about evidence/gaps? → Evidence matrix builder
5. Is it actually building/deploying? → Check ALL prerequisites
6. Are prerequisites satisfied? → Implementation skill (only if ALL yes)

**Tie-breaker:** "When in doubt, route to the skill that reduces uncertainty rather than the skill that mutates state."

## 5 Upstream-to-Downstream Patterns
| Pattern | From → To | Key Emphasis |
|---------|-----------|-------------|
| A | Orchestrator → Repo Truth | Mission boundary, target repos, read-only mandate |
| B | Orchestrator → Evidence Matrix | Source candidates, comparison scope, expected decision |
| C | Repo Truth → Evidence Matrix | Canonical file map, exact modules, repo/doc mismatches |
| D | Evidence Matrix → Implementation | Approved source, evidence status, no-go areas, authority |
| E | Orchestrator → Implementation | Full validated packet (rare — requires all upstream complete) |

## Rejection Format
```yaml
handoff_rejection:
  rejected_by: "<skill>"
  reason_code: MISSING_REPO_TRUTH | INSUFFICIENT_EVIDENCE | UNCLEAR_AUTHORITY | CONFLICTED_SOURCES | UNCLEAR_OBJECTIVE | OTHER
  reason_summary: "<explanation>"
  required_return_skill: "<skill>"
  exact_missing_items: ["<item>"]
  mutation_blocked: true
```

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY
- **Shard:** W-06 CogniMesh | **Thread:** T13
- **TokenBridge:** ACT=REQUIRED, INT=REQUIRED, CON=OPTIONAL
- **Sovereignty Score:** 1010
