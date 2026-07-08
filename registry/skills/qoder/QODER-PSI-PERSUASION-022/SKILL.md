---
name: QODER-PSI-PERSUASION-022
description: "PSI-DOMINION Persuasion Calibrator — eta_i composite scoring (ethics*0.4 + tone*0.3 + structure*0.3), banned-word lexicon with approved replacements, 6 persuasion techniques (Silent Authority, Hybrid Trust, Active Verification Questions, Cognitive Load Discipline, Non-Threat Posture, Outcome-First Structure), audience psychological profiling for 7 decision-maker types. Gate 6 threshold: eta >= 0.80. Use when calibrating persuasive content, checking tone compliance, or profiling audiences. Thread 13 — ACAI V2."
---

# PSI-DOMINION — Persuasion Calibrator (ACU-PSI-001)

## Core Formula
`eta_i = (ethics * 0.4) + (tone * 0.3) + (structure * 0.3)`
Gate 6 threshold: eta_i >= 0.80 required for argument inclusion.

## Banned-Word Lexicon

| Banned Word | Risk | Approved Replacement |
|-------------|------|---------------------|
| unfair | Adversarial tone | procedurally inconsistent |
| biased | Emotional | insufficiently objective |
| wrong | Adversarial | not supported by evidence |
| error | Defensive | discrepancy |
| trap | Adversarial | structural concern |
| mistake | Defensive | area requiring clarification |
| fail | Emotional | does not meet threshold |
| reject | Adversarial | not sustain the position |

## 6 Persuasion Techniques

1. **Silent Authority Doctrine:** Lead with institutional weight, never assert — let credentials speak
2. **Hybrid Trust:** Combine quantitative evidence with qualitative institutional narrative
3. **Active Verification Questions:** Frame challenges as questions the panel should ask themselves
4. **Cognitive Load Discipline:** Reduce complexity; each argument fits one decision frame
5. **Non-Threat Posture:** Never position as adversarial; position as helpful clarification
6. **Outcome-First Structure:** State desired outcome first, then evidence chain

## Audience Psychological Profiling (7 Types)

| Type | Approach | Tone Score | Key Risk |
|------|----------|-----------|----------|
| Technical Expert | Data-heavy, precise citations | 1.00 | Over-simplification |
| Administrative Leader | Outcome-focused, executive summary | 0.85 | Excessive detail |
| Legal Counsel | Rule-anchored, binary framing | 1.00 | Emotional language |
| Financial Officer | Quantified impact, cost-benefit | 0.85 | Vague claims |
| Academic Reviewer | Methodology-transparent, literature-grounded | 0.90 | Unsupported assertions |
| Government Official | Precedent-aware, jurisdiction-sensitive | 0.85 | Scope overreach |
| Board Member | Strategic framing, risk-aware | 0.80 | Technical jargon |

## Workflow

1. Receive draft content
2. Scan for banned words — flag and replace
3. Score ethics component (factual accuracy, no misrepresentation)
4. Score tone component (classify against tone scale)
5. Score structure component (classify against structure types)
6. Compute eta_i — flag if below 0.80
7. Match to audience type — recommend technique adjustments
8. Output: calibrated content + eta_i score + recommendations

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY
- **Shard:** W-05 IDRAK | **Thread:** T13
- **Sovereignty Score:** 1010 | **Module:** AcuteriumCore
