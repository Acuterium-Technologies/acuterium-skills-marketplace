---
name: task-recovery
description: "Handles task recovery after LLM failures using matrix-defined fallback chains. Manages retry attempts, tracks recovery state, and gracefully degrades through alternative models until task completion or max-attempt exhaustion. Use when: task failed; recover task; fallback model; retry; graceful degradation; recovery chain; alternative llm; max attempts"
---

<!-- Source doctrine: ACU-SKILL-PAN-007 (ACU-PAN-RECOVERY-001.md) — Acuterium proprietary. -->

# Task Recovery — Automatic Fallback & Recovery Handler

## Recovery Flow

```
Task Failure → Init Recovery State → Read fallback_llms from Matrix → Attempt Next Fallback → Success? Mark Recovered : Retry
```

## Core Functions

### `get_fallback_llms(llm_name) → List[str]`
Reads `sub_models[].fallback_llms` from LLM Ranking Matrix.
Default fallbacks: `["GPT-4o", "Claude 3.7 Sonnet"]`.

### `init_recovery(task_id, original_llm) → RecoveryState`
Creates recovery state tracking: original model, fallback chain, attempt counter, max 3 attempts.

### `attempt_recovery(task_id, error) → Optional[str]`
Returns next fallback model name, or None if max attempts exceeded.
Increments attempt counter and logs error for Feedback Loop.

### `mark_recovered(task_id)`
Flags task as successfully recovered. Updates Feedback Loop with resolution data.

## Golden Schema Dependency

Reads `sub_models[].fallback_llms` — every matrix entry MUST define fallback chains.

## Pan Integration

- **Phase 4 (EXECUTE)**: Catches execution failures, initiates recovery
- **Swarm Coordinator**: Releases failed node, reallocates via fallback
- **Feedback Loop**: Failed attempts generate `FeedbackType.ERROR` entries
- **Resource Allocator**: `reallocate()` method uses recovery chain
