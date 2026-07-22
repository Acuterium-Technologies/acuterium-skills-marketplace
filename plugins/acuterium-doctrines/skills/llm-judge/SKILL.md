---
name: llm-judge
description: "Evaluate and score LLM outputs for quality assurance across accuracy, relevance, coherence, completeness, and compliance dimensions. Powers the QA guardrail layer in the Pan orchestration pipeline. Validates outputs against Golden Schema criteria and enables comparative ranking of multi-model responses. Use when: evaluate output; score quality; judge response; compare models; qa audit; compliance check; accuracy score; hallucination check; output verification"
---

<!-- Source doctrine: ACU-SKILL-PAN-001 (ACU-PAN-JUDGE-001.md) — Acuterium proprietary. -->

# LLM Judge — Output Quality Evaluation Engine

## Purpose

The LLM Judge is the quality assurance backbone of the Pan orchestration framework
and the AcuTect-CODEX engine. It evaluates every LLM output across five standardized
criteria before results are accepted into the pipeline.

## Evaluation Criteria

| Criterion | Weight | Description | Threshold |
|-----------|--------|-------------|-----------|
| **Accuracy** | 0.25 | Factual correctness, data integrity, citation validity | ≥ 0.85 |
| **Relevance** | 0.20 | Task alignment, scope adherence, query coverage | ≥ 0.80 |
| **Coherence** | 0.20 | Logical flow, consistency, structural quality | ≥ 0.80 |
| **Completeness** | 0.20 | Coverage of required fields, no missing data | ≥ 0.80 |
| **Compliance** | 0.15 | Golden Schema alignment, format adherence | ≥ 0.85 |

## Core Functions

### `evaluate(output_id, llm_name, output, expected)`
Score a single LLM output. Returns an `Evaluation` dataclass with per-criterion
scores, overall weighted score, and generated feedback.

### `compare(output_ids)`
Compare multiple evaluated outputs and return the ID of the highest-scoring one.
Used by Meta Negotiation to select optimal responses in consensus strategies.

### `_generate_feedback(scores)`
Produce human-readable feedback identifying criteria below threshold.
Feeds into the Feedback Loop for corrective action generation.

## Integration Points

- **Pan Pipeline Phase 5 (EVALUATE)**: Called after every task execution
- **Resource Allocator**: Quality scores feed back to adjust model scoring weights
- **Feedback Loop**: Low scores trigger `FeedbackType.QUALITY` entries
- **Compliance Validator**: Scores validated against Golden Schema ranges (0-100)
- **Meta Negotiation**: Used for multi-model consensus resolution

## Golden Schema Alignment

Maps directly to the `scoring` block in the Golden Standard:
```
scoring.reasoning   → Accuracy criterion
scoring.creativity  → Coherence criterion  
scoring.accuracy    → Accuracy + Compliance criteria
scoring.speed       → (tracked separately via PerformanceTracker)
scoring.multimodal  → Relevance criterion for multimodal tasks
scoring.coding      → Accuracy + Completeness for code outputs
```

## Usage Pattern

```python
from orchestrator.llm_judge import LLMJudge

judge = LLMJudge(rules_path="compliance_rules.yaml")
evaluation = judge.evaluate(
    output_id="TASK-001-OUTPUT",
    llm_name="Claude Opus 4.6",
    output=model_response,
    expected=golden_reference
)

if evaluation.overall_score < 0.80:
    # Trigger fallback via Task Recovery
    fallback_model = recovery.attempt_recovery(task_id, error="quality_below_threshold")
```

## QA Guardrail Role

The LLM Judge is the enforcement mechanism for the Critical QA Guardrail.
After each phase in the war game plan, the Judge runs validation:
1. Scores all phase outputs against criteria
2. Checks Golden Schema field coverage
3. Flags any scoring values outside 0-100 range
4. Blocks phase advancement if overall score < 0.80
5. Generates corrective feedback for the Feedback Loop
