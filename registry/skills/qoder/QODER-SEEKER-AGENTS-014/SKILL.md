---
name: QODER-SEEKER-AGENTS-014
description: "Acuterium Seeker Autonomous Agents - self-operating multi-agent system for autonomous night-seeker operations. Runs sub-agent process flows with orchestration, evidence-before-action discipline, read-only discovery before mutation, structured handoff packets, and APASF-SPEC-001 compliance. Operates across Qwen, QoderWork, Claude Code, Perplexity Computer, ChatGPT-CODEX, and AcuTect-CODEX. Use when building autonomous agent workflows or self-directed multi-agent build pipelines. Thread 13 - ACAI V2."
---

# Acuterium Seeker Autonomous Agents

## Philosophy
Self-operating system modeled after OpenCrew and autonomous night agents. Runs by itself in multi-agent/sub-agent process flow with orchestration to build any future Acuterium system. Operates across 6 platforms: Qwen, QoderWork, Claude Code, Perplexity Computer, ChatGPT-CODEX, AcuTect-CODEX.

## Core Doctrine (APASF-SPEC-001)
1. Evidence before action - read-only discovery before any mutation
2. Structured output packets - YAML with built/partial/designed/aspirational/prohibited labeling
3. Handoff discipline - upstream produces packets, downstream validates before accepting
4. Anti-drift controls - checkpointing, resumable handoffs, mutation class gates (0-3)
5. Staleness rules - evidence expires, must be refreshed

## 11 Specialized Agent Roles
Session Governor (ACU-ORC-020), Swarm Lead (ACU-COORD-001), Release Orchestrator (ACU-ORC-012), Repo Truth Mapper (ACU-CON-021), Evidence Matrix Builder (ACU-CON-022), GitHub Evidence Auditor (ACU-CON-023), Policy Governance (ACU-GOV-002), Data Arabic Curator (ACU-DATA-003), Trainer Engineer (ACU-TRAIN-004), RLVR Eval Redteam (ACU-EVAL-005), Model Registry Governor (ACU-LUQ-012).

## Session Orchestration Flow
Discovery -> Evidence Matrix -> QA Gate -> Planning -> Approval -> Mutation -> Validation -> Release

## Handoff Packet Schema


## Mutation Class Gates
0: Read-only (no approval) | 1: Additive (self-approved) | 2: Modifying (peer review) | 3: Destructive (Swarm Lead + HITL)

## Night Seeker Pattern
1. Scope (read AGENTS.md, MEMORY.md, project state)
2. Map (repo truth mapper produces evidence matrix)
3. Plan (session governor creates phased plan)
4. Gate (pre-sweep QA risk assessment)
5. Execute (phase-by-phase with checkpointing)
6. Validate (red-team verification after each phase)
7. Handoff (structured packet for morning session)

## Decision Tree
Multi-repo? -> Swarm Lead | Code mutation? -> Repo Truth Mapper first | Evidence sufficient? -> Evidence Matrix Builder | Policy constraints? -> Policy Governance | Ready? -> Release Orchestrator

---

### APASF-SPEC-001 Appendix
- Classification: ACUTERIUM-PROPRIETARY | Shard: W-06 (CogniMesh) | Thread: T13
- Sovereignty Tier: 6 (ACAI V2, Claude Enterprise backbone)
- Output: { agents[], handoff_packets[], mutation_class, evidence_matrix, plan }
