---
name: qoder-urana-platform-010
description: "---"
---

<!-- Acuterium registry: qoder |  | category= | thread= -->

# URANA Platform Architecture

## Database Design
PostgreSQL + Supabase. Multi-tenant with UUID primary keys. Tables: tenants, users, memberships, projects, frameworks, standards, criteria, documents, evidence_links, assessments, criterion_results, appeals, appeal_claims, audit_log.

## Row-Level Security (RLS)
```sql
ALTER TABLE projects ENABLE ROW LEVEL SECURITY;
CREATE POLICY tenant_isolation ON projects USING (tenant_id = current_setting('app.current_tenant_id')::UUID);
```
All tenant-scoped tables enforce isolation via `app.current_tenant_id` session variable.

## Authentication Flow
Supabase Auth → `signUp` / `signInWithPassword` → JWT (15min expiry) + refresh token → memberships lookup → tenant context.

## AI Orchestrator
Multi-LLM routing: DeepSeek (legal/Arabic), Qwen (documents, cost-effective), Kimi (long context 128K), OpenAI (complex reasoning, fallback). Task-specific system prompts. Automatic fallback chain. Audit logging per query.

## Evidence Library
Documents stored in Cloudflare R2 / S3. SHA256 integrity hash. Confidentiality levels. Evidence links map documents to criteria with link_type (supports/contradicts/supplements).

## Audit Trail
Every mutation logged: tenant_id, actor_user_id, action, entity_type, entity_id, ip_address, metadata (JSONB).

## PWA Architecture
Service worker with cache-first for static, network-first for API. Push notifications. Background sync for offline submissions. Installable manifest.

## Tech Stack
React 18 + Vite + Tailwind + Supabase + Cloudflare R2 + Framer Motion + Lucide React + Recharts + TanStack Query + React Hook Form + Zod.

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY | **Shard:** W-09 (Baranurion) | **Thread:** T13
- **Sovereignty Tier:** 10 (Urana = air-gap only, Llama 4 / DeepSeek-R1)
- **Output:** `{ schema, auth, rls, orchestrator, evidence, audit }`
