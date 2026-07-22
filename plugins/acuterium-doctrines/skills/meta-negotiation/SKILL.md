---
name: meta-negotiation
description: "Negotiates optimal task-to-LLM assignments by scoring candidate models against task requirements using the LLM Ranking Matrix. Implements auction-style bidding where models compete on capability match, language support, uptime, and cost. Use when: negotiate model; select best llm; candidate scoring; model comparison; task routing; multi-model selection; auction; bid"
---

<!-- Source doctrine: ACU-SKILL-PAN-006 (ACU-PAN-NEGOTIATE-001.md) — Acuterium proprietary. -->

# Meta Negotiation — Multi-LLM Task Routing Negotiator

## Scoring Algorithm

```
score = base(0.5) + multimodal_match(0.2) + language_match(0.2) + uptime_bonus(0.1)
```

### `get_candidates(task_type, requirements) → List[Dict]`
Iterates all matrix `sub_models`, scores each against requirements, returns sorted list.

### `_score_candidate(model, requirements) → float`
Scores individual model: multimodal capability (+0.2), language match (+0.2),
uptime weighted (+0.1 * predictive_uptime_score). Capped at 1.0.

### `negotiate(task) → Dict`
Select best LLM with alternatives. Returns `{selected, provider, score, alternatives}`.
Default fallback: GPT-4o with reason "No matching candidates."

## Pan Integration
- Called by Resource Allocator during ALLOCATE phase
- Candidates feed into Swarm Coordinator AUCTION strategy
- Results recorded in Feedback Loop for weight optimization
