# Changelog — Acuterium Skills Marketplace

## [v8.1.0] — 2026-06-26 — QODER ACAI V2 Design System Collection (25 skills)

### Added — QODER Collection (`registry/skills/qoder/`, 25 files) — Thread T13 ACAI V2
Authored in QoderWork, adopted into the registry. Glassmorphic "Liquid Glass" design system,
cognitive engines, URANA platform, security, math, governance.
- `QODER-ACAI-DESIGN-001` · `QODER-DESIGN-TOKENS-002` · `QODER-GLASS-COMP-003` · `QODER-COGNITIVE-ENGINES-004`
- `QODER-MOTION-MORPH-005` · `QODER-WEB-IMPL-006` · `QODER-IOS-IMPL-007` · `QODER-ANDROID-IMPL-008`
- `QODER-SWARM-UI-BUILD-009` · `QODER-URANA-PLATFORM-010` · `QODER-Q-ENC-SECURITY-011` · `QODER-MAJD-CHAT-012`
- `QODER-ACUTECT-ORCHESTRATOR-013` · `QODER-SEEKER-AGENTS-014` · `QODER-AI-ORCHESTRATOR-015` · `QODER-BILINGUAL-RTL-016`
- `QODER-PWA-KIT-017` · `QODER-NEURO-ENGINE-018` · `QODER-SUPABASE-AUTH-019` · `QODER-MATH-ENGINES-020`
- `QODER-REDTEAM-QA-021` · `QODER-PSI-PERSUASION-022` · `QODER-SOVEREIGN-GOV-023` · `QODER-HANDOFF-PROTOCOL-024` · `QODER-LUQMANML-025`

### Added — Collection registration
- `registry/skills/qoder/INDEX.md` — collection index (ACU-SKILL-REGISTRY-QODER)
- `registry/skills/qoder/qoder-skills.json` — collection manifest (truthful fields from source frontmatter)

### Note
- Master `skills.json` (generated) is NOT hand-edited here — run the registry generator to fold the
  `qoder` collection into the master index and total count.

## [v8.0.0] — 2026-03-17 — Pan Framework + Commercial Products Release

### Added — Pan Framework Skills (9 files)
- `ACU-PAN-JUDGE-001.md` — LLM Judge: Output Quality Evaluation Engine
- `ACU-PAN-MATRIX-001.md` — LLM Matrix Loader: Unified Ranking Matrix Engine
- `ACU-PAN-ADOCP-001.md` — ADOCP: Dynamic Orchestration & Coordination Protocol
- `ACU-PAN-COMPLIANCE-001.md` — Compliance Rules Engine: Prometheus-Style Monitoring
- `ACU-PAN-CYBERDEF-001.md` — Erebus Cyber Defence: Sovereign Threat Intelligence
- `ACU-PAN-NEGOTIATE-001.md` — Meta Negotiation: Multi-LLM Task Routing
- `ACU-PAN-RECOVERY-001.md` — Task Recovery: Automatic Fallback Handler
- `ACU-PAN-DAG-001.md` — DAG Engine: Directed Acyclic Graph Execution
- `ACU-PAN-ORCHESTRATOR-001.md` — Pan Orchestrator (CrewAI, LangGraph, Events, Scheduler, Master Pipeline)

### Added — Commercial Product Skills (2 files)
- `ACU-MADA-001.md` — MADA Intelligence Briefing System (Flagship Commercial Tier 1)
- `ACU-URANA-001.md` — URANA Quality Management System (Flagship Commercial Tier 1)

### Updated
- `INDEX.md` — v1.0 → v2.0: Registry expanded from 8 → 19 proprietary skills
- Updated dependency map with MADA, URANA, and Pan Framework integration
- Updated shard deployment map (complete 19-skill mapping)
- Total Acuterium registry skills: 42 (Lawvable) + 19 (Proprietary) = 61

### QA Status
- All 19 files pass naming convention (`ACU-[MODULE]-[###].md`) ✅
- All 19 files pass frontmatter validation (required fields present) ✅
- All 19 files pass prohibited content check (zero Manus references) ✅
- All files ASIP v2 compliant, TokenBridge authorized

### Source Attribution
- Pan Framework skills authored by Claude Opus 4.6 (Pan Orchestration Engine)
- MADA/URANA skills authored by Acuterium Technologies Inc.
- QA validation and repo integration by Perplexity Computer


## [7.0.0] — 2026-03-09

### Added
- **37 new agent skills** (21 MCP Market + 16 Acuterium Proprietary Legal/QA/Audit/Compliance)
- MCP Market Skills (21): Comprehensive Research Agent, Deep Research Workflow, Perplexity Search Integration, ARK Research Intelligence, Hacker News Explorer, Advanced X/Twitter Intelligence, People Research & Discovery, Financial Report Advanced Search, Company Intelligence Research, Google Places Search, Firecrawl Web Scraper, USPTO Patent & Trademark Intelligence, Google Search Web Access, Agent Team Task Coordination, Multi-Agent Communication Protocols, Multi-Agent PR Reviewer, Swarm Intelligence Coordinator V3, Agentic Jujutsu Quantum-Resistant VCS, Z-AI Multimodal CLI, Reverse API Engineer, Perplexity AI Deep Search
- Legal AI Skills (5): Contract Review Agent, Legal Research Assistant, Legal Document Drafting Agent, Due Diligence Agent, E-Discovery Processing Agent
- Compliance AI Skills (5): Compliance Monitoring Agent, Regulatory Change Intelligence Agent, Policy Enforcement Agent, Risk Assessment Intelligence Agent, Compliance Workflow Automation Agent
- Audit AI Skills (3): Internal Audit Automation Agent, Automated Compliance Auditing Agent, Audit Trail & Evidence Management Agent
- Quality Assurance Skills (3): QA Quality Assurance Framework Agent, Accreditation & Attestation Intelligence Agent, CAPA Narrative Generator Agent
- APASF Framework V1 updated: Added Section 6.5 — Baranurion APMS (Adaptive Protocol Management System) integration protocol; fixed APMS nomenclature
- SKILL.md files for all 16 proprietary skills in skills/{legal-ai,compliance-ai,audit-ai,quality-assurance}/
- MCP Market handover report (ACU-HANDOVER-MCP-001) and implementation instructions in docs/
- IDs: ACU-SKILL-4086 through ACU-SKILL-4122

### Changed
- Skills registry total: 4,085 → 4,122
- Registry version: 6.0.0 → 7.0.0
- APASF Section 6 now covers 5 integration protocols: ADOCP, DIARAN-MOE, CogniMesh, TokenBridge, APMS

## [6.0.0] — 2026-03-09

### Added
- **113 new agent skills** (105 framework + 8 Acuterium proprietary)
- Framework skills: AutoGen Studio, OpenAI Agents SDK, Google ADK, LangGraph, CrewAI, Semantic Kernel, Haystack, Camel-AI, BabyAGI, SmolAgents, Dify
- 8 proprietary skills: RIA, PRISM-SIE, Q-ENC, THREAT, StratEdge, PSI, RedTeam, Cascade
- APASF Framework V1 (Acuterium Proprietary Agent Skill Framework)
- Keyword enrichment for 2,249 skills, status promotion for 2,179 draft→published
- SQL transaction wrappers with verification

### Changed
- Skills registry total: 3,972 → 4,085

## [5.0.0] — 2026-03-09

### Added
- **44 new agent skills** (42 Legal AI from lawvable/awesome-legal-skills + 2 MCP Market)
- Legal AI — Commercial Law: 6 skills (Contract Review, Debt Recovery, NDA Review/Triage, NIL Contracts, Tech Negotiation)
- Legal AI — Privacy Law: 6 skills (Cookie Policy, DPIA, GDPR Breach Sentinel, Privacy Compliance, Notice/Policy Drafting)
- Legal AI — Compliance: 2 skills (Vendor Due Diligence, Whistleblower Policy Auditor)
- Legal AI — Employment Law: 2 skills (Dismissal Challenge/Notification Drafters)
- Legal AI — Corporate Law: 1 skill (Shareholder Disclosure Enforcer)
- Legal AI — Legal Methodology: 6 skills (Legal Simulation, Mediation, Red Team Verifier, Risk Assessment x2, Statutory Interpretation)
- Legal AI — Legal Tooling: 3 skills (Canned Responses, Meeting Briefing, Tabular Review)
- Legal AI — MS Office: 9 skills (Excel x3, Outlook, PowerPoint, Word x4)
- Legal AI — Adobe: 2 skills (PDF Processing x2)
- Legal AI — Vibe-Coding: 2 skills (Security Review, VS Code Extension Builder)
- Legal AI — Meta-Skills: 3 skills (Skill Self-Creation x2, Skill Optimizer)
- MCP Market — Web Intelligence: 1 skill (Google Search & Web Access)
- MCP Market — Research Intelligence: 1 skill (Ark Research)
- Shard mappings: W-02 Ajraam (25), W-08 ZURD (7), EREBUS-CSE (4), Diaran-MOE (3), others
- URANA protocol mappings: URANA-RISK-001, URANA-AUDT-001, URANA-COMP-001, URANA-QMS-001
- 6 French-law skills flagged for Oman/GCC localization
- Updated skills.json (3,972 total), CSV master index, SQL seeds, Excel registry V5
- 2 duplicates excluded: Agent Team Task Coordination, Team Communication Protocols (already in v4)

### Changed
- Skills registry total: 3,928 → 3,972
- skills.json schema: added ruzn_module, urana_module, erebus_integration, priority, localization_flag fields

## [4.0.0] — 2026-03-09

### Added
- 1,740 new agent skills from MCP Market, dmgrok catalog, awesome-agent-skills, anthropic cookbooks/courses, obra/superpowers
- Registry total: 2,188 → 3,928

## [3.0.0] — 2026-03-09

### Added
- 2,179 new agent skills from 21 GitHub repositories
- Registry total: 9 → 2,188

## [0.1.0] — 2026-03-09

### Added
- Initial marketplace architecture (Registry, Discovery, Infusion services)
- Skill manifest specification (SKILL.md format)
- Registry of 9 existing agent skills
- Database schema extending APMS
- Docker Compose deployment configuration
- CLI tool stub
- API reference documentation
- BARANURION governance integration points
- ASIP infusion ceremony workflow
