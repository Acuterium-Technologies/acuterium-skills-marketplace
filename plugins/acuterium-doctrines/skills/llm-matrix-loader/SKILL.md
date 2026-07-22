---
name: llm-matrix-loader
description: "Load, normalize, query, and validate the Acuterium LLM Ranking Matrix. Supports both legacy (Master_LLMs_Ranking_Matrix.json) and current (Acuterium_Final_LLM_Ranking_Matrix.json) formats. Normalizes all data into Golden Schema format for ADOCP routing consumption. Use when: load matrix; llm ranking; model scores; matrix query; normalize models; golden schema; provider lookup; model comparison; cost lookup; uptime score"
---

<!-- Source doctrine: ACU-SKILL-PAN-002 (ACU-PAN-MATRIX-001.md) — Acuterium proprietary. -->

# LLM Matrix Loader — Unified Ranking Matrix Engine

## Purpose

The LLM Matrix Loader is the data access layer for the entire Acuterium AI
orchestration ecosystem. Every routing decision, allocation, and scoring
operation depends on this module to provide consistent, validated matrix data.

## Supported Formats

### Format A: Legacy Grouped (Master_LLMs_Ranking_Matrix.json)
```json
{
  "matrix": [
    {
      "llm": "OpenAI",
      "sub_models": [...],
      "consciousness": {...},
      "capabilities": {...},
      "performance": {...},
      "scoring": {...}
    }
  ]
}
```

### Format B: Flat Models (Acuterium_Final_LLM_Ranking_Matrix.json)
```json
{
  "metadata": {...},
  "models": {
    "GPT-4o": { "model": "...", "provider": "OpenAI", ... },
    "Claude 3.7 Opus": { "model": "...", "provider": "Anthropic", ... }
  }
}
```

### Format C: Golden Schema (Target — Acuterium_Master_LLM_Ranking_Matrix_Golden-Rule_Schema.json)
Provider-grouped `matrix[]` array with ALL required fields:
`llm`, `sub_models`, `consciousness`, `capabilities`, `performance`, `scoring`

## Core Functions

### `load_llm_matrix(path)`
Load matrix from JSON file. Auto-detects format (A, B, or C) and returns
normalized data structure.

### Normalization Rules
- Format B → Format C: Group flat models by `provider` field, construct
  provider-level `consciousness`, `capabilities`, `performance`, `scoring` blocks
- Format A → Format C: Map legacy field names, add missing Golden Schema fields as N/A
- Duplicate detection: Models appearing in both legacy files are merged (newer data wins)
- Placeholder handling: Entries with only `provider` and `note` fields are flagged as incomplete

## Required Fields per Golden Schema

Every loaded matrix entry MUST contain or explicitly mark N/A:
1. `llm` (string) — Provider name
2. `sub_models[]` — Array with: `model`, `api_key`, `cost`, `deepresearch`, `predictive_uptime_score`
3. `consciousness` — `compatibility`, `reasoning_depth`, `ethical_alignment`
4. `capabilities` — `reasoning`, `cognition`, `multimodal`, `document_handling`, `code_generation`
5. `performance` — `latency`, `hallucination_rate`, `accuracy`
6. `scoring` — `reasoning`, `creativity`, `accuracy`, `speed`, `multimodal`, `coding`

## Integration Points

- **ADOCP Router**: Primary consumer — routes tasks to optimal LLMs based on matrix scores
- **Resource Allocator**: Scores candidates using matrix `scoring` and `cost` data
- **Swarm Coordinator**: Auto-registers swarm nodes from `sub_models` entries
- **Meta Negotiation**: Queries candidates and scores for task-type matching
- **Task Recovery**: Reads `fallback_llms` arrays for recovery chain construction
- **Event Triggers**: Loads matrix for model selection on event processing
- **Compliance Validator**: Validates loaded matrix against Golden Schema structure

## Data Integrity Rules

1. Never delete legacy entries unless officially confirmed discontinued
2. Scoring values must be 0-100 range (validated on load)
3. Cost values must be non-negative USD per 1K tokens
4. `predictive_uptime_score` must be 0.0–1.0
5. `fallback_llms` must reference models that exist in the matrix
6. Placeholder entries preserved but flagged with `_placeholder: true`
