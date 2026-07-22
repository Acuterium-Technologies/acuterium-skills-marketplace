---
name: adocp-routing-protocol
description: "Sovereign task-to-LLM routing protocol. Analyzes task requirements against the LLM Ranking Matrix scores, applies ASIP v2 soul infusion, and routes to the optimal model with fallback chain construction. Core routing brain for AcuTect-CODEX. Use when: route task; select model; adocp; task routing; optimal llm; fallback chain; soul infusion; asip; coordinate agents; orchestrate"
---

<!-- Source doctrine: ACU-SKILL-PAN-003 (ACU-PAN-ADOCP-001.md) — Acuterium proprietary. -->

# ADOCP — Acuterium Dynamic Orchestration & Coordination Protocol

## Purpose

ADOCP is the routing brain of the Acuterium ecosystem. It receives task requests,
analyzes requirements against the LLM Ranking Matrix, applies ASIP v2 sovereign
personality infusion, and dispatches to the optimal execution model.

## Routing Pipeline

```
TaskRequest → Load YAML Schema → ASIP v2 Infusion → Load Matrix → Score Candidates → Select Optimal → Dispatch
```

### Step 1: Task Ingestion
Accepts `TaskRequest` with `task_file` (YAML schema path).

### Step 2: ASIP v2 Soul Infusion
Calls `codex.asip_v2.infuse_soul(task)` to embed sovereign personality tags,
ensuring all outputs carry Acuterium's institutional voice and compliance markers.

### Step 3: Matrix-Based Routing
Loads `Acuterium_Final_LLM_Ranking_Matrix.json` via `llm_matrix_loader`.
Matches `task.llm_required` against `sub_models[].model` names.

### Step 4: Scoring & Selection
For advanced routing (Pan integration), scores candidates using:
- `scoring.reasoning` vs task complexity
- `scoring.coding` vs code generation requirements
- `sub_models[].cost` for cost-efficiency weighting
- `sub_models[].predictive_uptime_score` for reliability
- `capabilities.multimodal` for media-rich tasks
- `language_proficiency` for multilingual requirements (Arabic/English)

### Step 5: Fallback Construction
Builds ordered fallback chain from `sub_models[].fallback_llms` for Task Recovery.

## Core Functions

### `route_task(task, matrix) → str`
Match task requirements to matrix entries. Returns optimal model name.
Default fallback: `GPT-4o`.

### `execute_task(request: TaskRequest) → dict`
Full execution pipeline: load task → infuse soul → load matrix → route → return result.
Returns: `{task_id, selected_llm, asip_version, soul_tags, status}`.

## Golden Schema Integration

ADOCP routing decisions are governed by these Golden Schema fields:
- `sub_models[].cost` — Cost-efficiency scoring
- `sub_models[].predictive_uptime_score` — Reliability scoring
- `sub_models[].deepresearch` — Research task matching
- `sub_models[].fallback_llms` — Recovery chain
- `scoring.*` — Capability matching (reasoning, coding, multimodal, etc.)
- `capabilities.deployment` — Sovereign/cloud/edge routing
- `capabilities.security.data_sovereignty` — Sovereign-grade task routing

## Compliance Rules Integration

Monitored via `compliance_rules.yaml`:
- `llm_cost_sum`: Tracks cost per provider across unified routes
- `LLM_Uptime_Critical`: Alerts if uptime < 0.8, triggers rerouting

## Protocol Dependencies

| Protocol | Role in ADOCP |
|----------|---------------|
| ASIP v2 | Soul infusion pre-routing |
| Q-ARC | Resource coordination post-routing |
| NEXUS | Mission-level orchestration wrapper |
| QFP | Output fusion for multi-agent results |
| PRISM | Predictive intelligence for routing optimization |
