---
name: legal-research-assistant
description: "Sovereign AI agent for comprehensive legal research across Omani statutes, GCC regulatory frameworks, and international legal precedents. Supports natural language querying in Arabic and English, with automated research memo generation and citation management. Use when: legal research; case law search; statute lookup; precedent analysis; legal citation; research memo"
---

<!-- Source: ACU-SKILL-LEG-002 — Acuterium legal-ai, proprietary. -->

# Legal Research Assistant — SKILL.md

## 1. Purpose

Sovereign AI agent for comprehensive legal research across Omani statutes, GCC regulatory frameworks, and international legal precedents. Supports natural language querying in Arabic and English, with automated research memo generation and citation management.

## 2. Domain Mapping

| Dimension | Value |
|---|---|
| **Primary Platform** | RUZN.AI — Sovereign Legal Intelligence |
| **Secondary Platform** | Ūrānā — Regulatory Intelligence |
| **HISN AL-WUJŪD Shard** | C-01 (RUZN-GOV) |
| **DIARAN-MOE Expert Cluster** | Legal-Research-001 through Legal-Research-008 |
| **Sovereignty Tier** | 10/10 |
| **Arabic NLP Engine** | Qwen-2.5 |
| **Reasoning Engine** | DeepSeek-R1 |

## 3. Capabilities

- Searches across sovereign legal databases via natural language queries (Arabic/English)
- Retrieves and summarizes relevant case law, Royal Decrees, ministerial decisions
- Identifies supporting and distinguishing precedents with confidence scoring
- Tracks recent legislative developments across Omani and GCC jurisdictions
- Generates structured research memos with proper legal citations
- Cross-references statutes with implementing regulations and judicial interpretations
- Maintains a sovereign legal knowledge graph updated from official gazette feeds

## 4. Implementation Architecture

```typescript
interface LegalResearchQuery {
  query: string;
  language: 'ar' | 'en';
  jurisdiction: 'OM' | 'AE' | 'SA' | 'BH' | 'QA' | 'KW' | 'GCC_ALL';
  legalDomain: 'commercial' | 'criminal' | 'administrative' | 'labor' | 'constitutional' | 'regulatory';
  dateRange?: { from: string; to: string };
  maxResults: number;
}

interface ResearchResult {
  sources: LegalSource[];
  memo: StructuredMemo;
  citations: LegalCitation[];
  precedentGraph: PrecedentRelationship[];
  confidenceScore: number;
}

interface LegalSource {
  type: 'royal_decree' | 'ministerial_decision' | 'court_ruling' | 'regulation' | 'gcc_treaty';
  reference: string;       // e.g., "Royal Decree 111/2011, Article 7"
  relevanceScore: number;
  summary_ar: string;
  summary_en: string;
  holdingOrRatio: string;
}

// Core research pipeline
async function conductResearch(
  query: LegalResearchQuery
): Promise<ResearchResult> {
  const parsed = await parseNaturalLanguageQuery(query);
  const sources = await searchSovereignDatabase(parsed);
  const ranked = await rankByRelevance(sources, query);
  const precedents = await buildPrecedentGraph(ranked);
  const memo = await generateResearchMemo(ranked, precedents, query.language);
  await logAuditTrail('legal-research', query, memo);
  return { sources: ranked, memo, citations: extractCitations(ranked), precedentGraph: precedents, confidenceScore: memo.confidence };
}
```

## 5. Trigger Keywords

```
legal research, case law, statute lookup, precedent analysis, legal citation,
research memo, judicial ruling, royal decree search, ministerial decision,
regulatory analysis, legislative tracking, legal knowledge graph,
بحث قانوني, سوابق قضائية, تحليل التشريعات, مرسوم سلطاني, قرار وزاري,
تتبع التشريعات, استعلام قانوني
```

## 6. Sovereignty Rules

1. All legal databases hosted on sovereign infrastructure
2. Official gazette feeds ingested via secure sovereign pipeline
3. No third-party legal research API calls permitted at runtime
4. Research memos stored in HISN AL-WUJŪD encrypted document vault
5. Human-in-the-loop required for memo finalization and client delivery

## 7. Integration Points

- **RUZN.AI Legal Counsel Module**: Primary research interface
- **Ūrānā Regulatory Iron Dome**: Feeds regulatory change intelligence
- **NAHRĀ Browser**: Secure browsing for supplementary research
- **ACAI V2 KAIROS Module**: Temporal analysis of legislative evolution

## 8. Quality Metrics

| Metric | Target |
|---|---|
| Source retrieval precision | ≥ 93% |
| Citation accuracy | ≥ 98% |
| Precedent relevance scoring | ≥ 90% |
| Research time reduction | ≥ 80% vs manual |
| Bilingual memo quality | ≥ 95% human-equivalent |

## 9. References

- MindStudio: AI Agents for Legal Professionals — Legal Research Assistant (2026)
- Acuterium RUZN Protocol — Omani Legal Knowledge Base
- Royal Decree 111/2011, Royal Decree 112/2011
- National Integrity Plan 2022-2030
