---
name: e-discovery-processing-agent
description: "Sovereign AI agent for processing electronic evidence in litigation and regulatory investigations. Organizes, indexes, searches, and tags digital evidence (emails, documents, chat logs, data files) with intelligent relevance filtering and privilege detection. Use when: e-discovery; electronic evidence; document review; privilege detection; litigation support"
---

<!-- Source: ACU-SKILL-LEG-005 — Acuterium legal-ai, proprietary. -->

# E-Discovery Processing Agent — SKILL.md

## 1. Purpose

Sovereign AI agent for processing electronic evidence in litigation and regulatory investigations. Organizes, indexes, searches, and tags digital evidence (emails, documents, chat logs, data files) with intelligent relevance filtering and privilege detection. All processing occurs on sovereign infrastructure with zero cloud exposure.

## 2. Capabilities

- Processes and indexes large volumes of electronic data (100K+ items)
- Applies relevance filters based on case issues and custodian profiles
- Tags documents with topics, parties, date ranges, and privilege markers
- Identifies potentially privileged communications (attorney-client, work product)
- Reduces document sets to reviewable sizes (60-80% reduction target)
- Supports Arabic and English document corpus with mixed-language detection
- Generates production sets with Bates numbering and metadata export
- Maintains chain of custody records per Ūrānā Evidence Locker standards

## 3. Implementation Architecture

```typescript
interface EDiscoveryConfig {
  caseId: string;
  custodians: string[];
  dataSourceTypes: ('email' | 'documents' | 'chat' | 'financial' | 'database')[];
  searchTerms: string[];
  dateRange: { from: string; to: string };
  privilegeTerms: string[];
  relevanceModel: 'keyword' | 'semantic' | 'hybrid_ai';
}

async function processEDiscovery(config: EDiscoveryConfig): Promise<EDiscoveryResult> {
  const ingested = await ingestDataSources(config.dataSourceTypes, config.custodians);
  const indexed = await indexAndDeduplicate(ingested);
  const filtered = await applyRelevanceFiltering(indexed, config.searchTerms, config.relevanceModel);
  const privilegeTagged = await detectPrivilege(filtered, config.privilegeTerms);
  const tagged = await applyTopicTags(privilegeTagged);
  const productionSet = await generateProductionSet(tagged);
  await maintainChainOfCustody(productionSet, config.caseId);
  return { totalProcessed: ingested.length, relevant: filtered.length, privileged: privilegeTagged.filter(d => d.isPrivileged).length, productionSet };
}
```

## 4. Quality Metrics

| Metric | Target |
|---|---|
| Document classification accuracy | ≥ 94% |
| Privilege detection recall | ≥ 98% |
| Document set reduction | ≥ 65% |
| Processing throughput | 10K docs/hour |
