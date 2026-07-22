---
name: qoder-luqmanml-025
description: "| ID | Name | Shard | Purpose | |----|------|-------|---------| | LUQ-001 | luqmanml-training-orchestrator | W-01 Diaran | Master coordinator for all LuqmanML workflows | | LUQ-002 | luqmanml-doctrine-infuser | W-05 IDRAK | Encodes doctrine, tone, ethics, identity into datasets and rewards | | LUQ-003 | luqmanml-dataset-governor | W-03 Watad | Ingestion, provenance, labeling, splits, residency, contamination | | LUQ-004 | luqmanml-sft-pipeline | W-03 Watad | Builds and validates supervised fine-tuning pipelines | | LUQ-005 | luqmanml-rlvr-engine | W-05 IDRAK | Reward design and verifiable optimization | | LUQ-006 | luqmanml-distillation-engine | W-01 Diaran | Teacher-student distillation and synthetic reasoning | | LUQ-007 | luqmanml-embedding-encoder-governor | W-03..."
---

<!-- Acuterium registry: qoder |  | category= | thread= -->

# LuqmanML Sovereign Training Skill Family

## 19 Skills Inventory

| ID | Name | Shard | Purpose |
|----|------|-------|---------|
| LUQ-001 | luqmanml-training-orchestrator | W-01 Diaran | Master coordinator for all LuqmanML workflows |
| LUQ-002 | luqmanml-doctrine-infuser | W-05 IDRAK | Encodes doctrine, tone, ethics, identity into datasets and rewards |
| LUQ-003 | luqmanml-dataset-governor | W-03 Watad | Ingestion, provenance, labeling, splits, residency, contamination |
| LUQ-004 | luqmanml-sft-pipeline | W-03 Watad | Builds and validates supervised fine-tuning pipelines |
| LUQ-005 | luqmanml-rlvr-engine | W-05 IDRAK | Reward design and verifiable optimization |
| LUQ-006 | luqmanml-distillation-engine | W-01 Diaran | Teacher-student distillation and synthetic reasoning |
| LUQ-007 | luqmanml-embedding-encoder-governor | W-03 Watad | Non-generative encoder training and evaluation |
| LUQ-008 | luqmanml-eval-benchmark-suite | W-08 ZURD | Benchmarks, adversarial tests, drift checks, release scoring |
| LUQ-009 | luqmanml-arabic-first-curator | W-02 Ajraam | Arabic-first, GCC-aware data and evals |
| LUQ-010 | luqmanml-release-gatekeeper | W-09 Baranurion | Sovereign release gates before checkpoint promotion |
| LUQ-011 | luqmanml-nano-model-forge | W-01 Diaran | Small sovereign models for specialized functions |
| LUQ-012 | luqmanml-model-registry-governor | W-09 Baranurion | Checkpoint lineage, metadata, compatibility, approval |
| LUQ-013 | luqmanml-skill-author | W-01 Diaran | Generates new LuqmanML skills using APASF-SPEC-001 |
| LUQ-014 | luqmanml-rlvr-agentic-alignment | W-05 IDRAK | GRPO, trajectory reward, agentic RL control |
| LUQ-015 | luqmanml-hmadam-resource-optimizer | W-03 Watad | Half-memory Adam optimizer, GPU budget policy |
| LUQ-016 | luqmanml-moe-cot-distiller | W-01 Diaran | Sparse MoE and Arabic-first CoT distillation |
| LUQ-017 | luqmanml-stage-loss-masking | W-08 ZURD | Hallucination filtering, verified-step masking |
| LUQ-018 | luqmanml-hybrid-context-architect | W-01 Diaran | Mamba-Transformer hybrid long-context policy |
| LUQ-019 | luqmanml-dynamic-betterrag-sync | W-09 Baranurion | RAG refresh instead of needless retraining |

## 7-Phase Creation Sequence

| Phase | Build | Rationale |
|-------|-------|-----------|
| 1 | LUQ-013 (skill-author) | Ensures all later skills follow one standard |
| 2 | LUQ-001 (orchestrator) | Establishes the master coordinator |
| 3 | LUQ-002 (doctrine) + LUQ-003 (dataset) | Locks doctrine and corpus governance early |
| 4 | LUQ-004 (SFT) + LUQ-006 (distillation) | Builds core training mechanics |
| 5 | LUQ-005 (RLVR) + LUQ-008 (eval) | Adds reward and evaluation rigor |
| 6 | LUQ-012 (registry) + LUQ-010 (release) | Enables governed release and checkpoint lifecycle |
| 7 | LUQ-009 (Arabic) + LUQ-007 (encoder) + LUQ-011 (nano) | Domain expansion after foundations |

## Naming Convention
- `acu_skill_id`: `ACU-LUQ-NNN`
- `name`: `luqmanml-<function>-<role>`
- `module`: `LuqmanML`
- `license`: `Proprietary-ACU`
- `registry_version`: `ACU-R1.0`

## APASF-SPEC-001 Compliance (~22-28 frontmatter fields)
Required: acu_skill_id, version, registry_version, taxonomy, security_classification, license, trigger_keywords[], primary_shard, compatible_shards[], platforms[], author, tokenbridge_requirements{ACT,INT,CON}, sqs, sss, sci

## Lifecycle Path
DRAFT → REVIEW (5-Gate QA via URANA QMS, SQS >= 6.5) → PUBLISHED (assign ACU-SID) → DEPLOYED (Baranurion/TokenBridge)

## Key Governance Rules
- No dependence on Falcon, ALLaM, or GCC-branded base-model identity sources
- Arabic is the native reasoning frame, not a translation veneer
- OMAN data residency preserved throughout
- All checkpoints require signed CWH attestation
- CGM/OCF governance separation enforced

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY
- **Shard:** W-01 Diaran-MOE (primary) | **Thread:** T13
- **TokenBridge:** ACT=REQUIRED, INT=REQUIRED, CON=OPTIONAL
- **Sovereignty Score:** 1010 | **Module:** LuqmanML
- **Data Residency:** OMAN
