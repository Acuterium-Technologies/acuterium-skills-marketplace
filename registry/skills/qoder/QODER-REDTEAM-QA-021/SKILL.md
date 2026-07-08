---
name: QODER-REDTEAM-QA-021
description: "Acuterium adversarial verification engine — 8-Gate Audit Matrix (Admissibility, Regulatory Precision, Scope-Lock, PJS Bypass, Evidence-Lock, Tone Compliance, Cascade Integrity, Red-Team Survival). 5 adversarial personas (Opposing Counsel, Panel Chair, Regulatory Solicitor, Statistical Adversary, Internal Devil's Advocate). Distribution Readiness Certificates (72-hour validity). Argument Survival Scores (0-100). Use when verifying outputs, running QA audits, or red-teaming deliverables. Thread 13 — ACAI V2."
---

# REDTEAM — 8-Gate Adversarial QA (ACU-REDTEAM-001)

## 8-Gate Audit Matrix

| Gate | Name | Pass Criteria | Fail Action |
|------|------|---------------|-------------|
| 1 | Admissibility | All evidence pre-deadline, cited in framework | Exclude argument entirely |
| 2 | Regulatory Precision | Every claim maps to specific rule/standard clause | Reclassify or remove |
| 3 | Scope-Lock | Arguments within defined appeal/review boundaries | Flag scope violation |
| 4 | PJS Bypass | R_i classification validated per decision tree | Reclassify resistance |
| 5 | Evidence-Lock | ES_i >= 0.50 for all included arguments | Downgrade or exclude |
| 6 | Tone Compliance | eta_i >= 0.80 (no banned words, proper structure) | Rewrite or exclude |
| 7 | Cascade Integrity | CASCADE P_goal computation verified against P_adj inputs | Recompute |
| 8 | Red-Team Survival | Argument survives all 5 adversarial personas | Flag as vulnerable |

## 5 Adversarial Personas

1. **Opposing Counsel:** Attacks evidence quality, finds procedural gaps, challenges admissibility
2. **Panel Chair:** Questions scope compliance, regulatory precision, institutional context
3. **Regulatory Solicitor:** Tests framework alignment, precedent consistency, jurisdictional issues
4. **Statistical Adversary:** Challenges P_base calibration, ES_i scoring, Monte Carlo assumptions
5. **Internal Devil's Advocate:** Stress-tests logic chains, finds internal contradictions

## Argument Survival Score (0-100)

`ASS_i = (Gate_Pass_Count / 8) * 100 * Survival_Factor`
- Survival_Factor: proportion of adversarial personas that fail to defeat the argument
- Threshold: ASS >= 70 for inclusion in final deliverable

## Distribution Readiness Certificate

- Valid for 72 hours from issuance
- Requires all 8 gates passed
- Requires minimum ASS >= 70 across all arguments
- Requires sign-off from both automated and human review
- Includes: timestamp, gate results summary, adversarial test results, recommended actions

## Integration Points

- Called by RIA after EQ-5 (CASCADE feeds Gate 7)
- Called by PRISM after sensitivity analysis (Gate 8)
- Called by PSI after tone compliance check (Gate 6)
- Output feeds final deliverable assembly

## Workflow

1. Receive argument set with P_adj, ES_i, eta_i scores
2. Run each argument through all 8 gates sequentially
3. Compute Argument Survival Score per argument
4. Run 5 adversarial personas on arguments passing Gates 1-7
5. Generate Distribution Readiness Certificate (if all pass)
6. Output: certified arguments + vulnerable arguments + recommended fixes

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY
- **Shard:** EREBUS-CSE | **Thread:** T13
- **Sovereignty Score:** 1010 | **Module:** AcuteriumCore
