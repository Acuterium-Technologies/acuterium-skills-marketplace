---
name: crewai-executor
description: "Execute tasks using CrewAI multi-agent framework. Manages agent crews with defined roles, goals, and backstories. Supports sequential and parallel task execution across agent teams. Use when: crewai; crew; multi-agent task; agent roles; collaborative execution"
---

<!-- Source doctrine: ACU-SKILL-PAN-009 (ACU-PAN-ORCHESTRATOR-001.md) — Acuterium proprietary. -->

# CrewAI Executor

## Architecture
Agent dataclass: `{name, role, goal, backstory}`
Task dataclass: `{description, agent, expected_output}`

## Core Functions

### `add_agent(name, role, goal, backstory)`
Register an agent with defined expertise and mission.

### `add_task(description, agent, expected_output)`
Assign a task to a specific agent.

### `execute() → Dict`
Execute all tasks with the crew. Returns `{crew_size, tasks_completed, results[]}`.

## Pan Integration
Used for COMPLEX/SOVEREIGN tasks where the Swarm Coordinator selects CONSENSUS or HIERARCHICAL strategy.
Related registry: ACU-SKILL-0396 (CrewAI), ACU-SKILL-3120 (CrewAI Multi-Agent Orchestration).

---

## LangGraph Executor (ACU-SKILL-PAN-010)

### Purpose
Execute multi-step tasks as stateful graph traversals using LangGraph framework.
Nodes are processing functions, edges define execution flow, state accumulates through the graph.

### Architecture
`GraphState`: `{input_data, output_data, current_node, history[]}`
Execution: Start node → process → follow edge → next node → until "end"

### Core Functions
- `add_node(name, func)` — Register processing function
- `add_edge(from_node, to_node)` — Define flow between nodes
- `execute(initial_state) → {output, history}` — Full graph traversal

### Pan Integration
Used for stateful multi-step workflows where intermediate state must persist.
Related registry: ACU-SKILL-0694 (LangGraph), ACU-SKILL-0721 (LLM Application Dev LangChain Agent).

---

## Event Triggers (ACU-SKILL-PAN-011)

### Purpose
Automated task triggering based on event conditions. Monitors system events
and fires registered actions when conditions are met.

### Architecture
`EventTrigger`: `{trigger_id, event_type, conditions, action, enabled}`
`EventTriggerManager`: Maintains registry of triggers and handlers.

### Core Functions
- `register_trigger(trigger)` — Register new event trigger
- `register_handler(event_type, handler)` — Bind handler to event type
- `check_conditions(trigger, event_data) → bool` — Evaluate conditions
- `process_event(event_type, event_data) → List[str]` — Fire matching triggers

### Pan Integration
- Triggers swarm rebalancing when node health degrades
- Fires compliance alerts from `compliance_rules.yaml` thresholds
- Auto-generates new subtasks from real-time data updates
- Loads LLM matrix for model selection within event handlers

---

## Task Scheduler (ACU-SKILL-PAN-012)

### Purpose
Redis-backed priority task queue. Manages task scheduling with 4 priority levels,
retry logic, and ordered execution.

### Priority Levels
`LOW(1)` | `MEDIUM(2)` | `HIGH(3)` | `CRITICAL(4)`

### Core Functions
- `schedule(task_id, task_data, priority) → str` — Insert task by priority
- `get_next() → ScheduledTask` — Pop highest-priority task
- `mark_complete(task_id)` — Mark done
- `mark_failed(task_id, retry=True)` — Fail with optional retry (max 3)

### Pan Integration
Feeds into Pan Pipeline as the entry queue. Task Categorizer pulls from scheduler,
categorizes, and hands to Resource Allocator.

---

## Pan Orchestrator (ACU-SKILL-PAN-013)

### Purpose
Master orchestration skill. Defines the full 8-phase execution pipeline and
QA guardrail procedures for the Pan framework.

### Pipeline Phases
1. INGEST → 2. CATEGORIZE → 3. ALLOCATE → 4. DISTRIBUTE → 5. EXECUTE → 6. EVALUATE → 7. FEEDBACK → 8. ADJUST

### QA Guardrail (runs after phases 1-3)
- Golden Schema compliance validation
- Required field verification
- Scoring range validation (0-100)
- Phase advancement blocking on failure

### Component Integration
Unifies: TaskCategorizer, ResourceAllocator, PerformanceTracker, AdaptiveOptimizer,
ComplianceValidator, SwarmCoordinator, FeedbackCollector, FeedbackAnalyzer.

### Golden Schema: Source of Truth
File: `Acuterium_Master_LLM_Ranking_Matrix_Golden-Rule_Schema.json`
All operations validated against this schema. No phase advances without QA PASS.
