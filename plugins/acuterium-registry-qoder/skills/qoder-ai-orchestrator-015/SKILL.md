---
name: qoder-ai-orchestrator-015
description: "| Provider | Base URL | Models | Priority | Best For | |----------|----------|--------|----------|----------| | DeepSeek | api.deepseek.com/v1 | deepseek-chat, deepseek-coder | 1 | Legal analysis, Arabic NLP | | Qwen | dashscope.aliyuncs.com/api/v1 | qwen-turbo, qwen-plus, qwen-max | 2 | Document analysis, cost-effective | | Kimi | api.moonshot.cn/v1 | moonshot-v1-8k, moonshot-v1-32k, moonshot-v1-128k | 3 | Long context (128K), large documents | | OpenAI | api.openai.com/v1 | gpt-4-turbo, gpt-4, gpt-3.5-turbo | 4 | Complex reasoning, fallback |"
---

<!-- Acuterium registry: qoder |  | category= | thread= -->

# Multi-Provider AI Orchestrator

## Provider Configuration

| Provider | Base URL | Models | Priority | Best For |
|----------|----------|--------|----------|----------|
| DeepSeek | api.deepseek.com/v1 | deepseek-chat, deepseek-coder | 1 | Legal analysis, Arabic NLP |
| Qwen | dashscope.aliyuncs.com/api/v1 | qwen-turbo, qwen-plus, qwen-max | 2 | Document analysis, cost-effective |
| Kimi | api.moonshot.cn/v1 | moonshot-v1-8k, moonshot-v1-32k, moonshot-v1-128k | 3 | Long context (128K), large documents |
| OpenAI | api.openai.com/v1 | gpt-4-turbo, gpt-4, gpt-3.5-turbo | 4 | Complex reasoning, fallback |

## Task-to-Provider Routing

```javascript
const ROUTING_MAP = {
  'legal-analysis':     ['deepseek', 'openai'],
  'regulatory-review':  ['deepseek', 'qwen'],
  'document-analysis':  ['kimi', 'openai'],     // Kimi for long docs
  'qa-review':          ['qwen', 'openai'],
  'risk-assessment':    ['deepseek', 'kimi'],
  'general':            ['deepseek', 'openai'],
};
```

## Core Orchestration Pattern

```javascript
class AIOrchestrator {
  async query(prompt, context = {}, options = {}) {
    const { taskType = 'general', provider = 'auto', maxTokens = 4000, temperature = 0.7 } = options;
    const selected = this.selectProvider(taskType, provider);
    try {
      const systemPrompt = this.getSystemPrompt(taskType, context);
      const response = await this.callProvider(selected, systemPrompt, prompt, { maxTokens, temperature });
      await this.logAudit({ provider: selected.name, taskType, tokensUsed: response.usage?.total_tokens || 0 });
      return { success: true, data: response, provider: selected.name, model: response.model, usage: response.usage };
    } catch (error) {
      if (provider === 'auto') {
        const fallback = this.getFallbackProvider(selected);
        if (fallback) return this.query(prompt, context, { ...options, provider: fallback.name.toLowerCase() });
      }
      throw new Error(`AI Service Unavailable: ${error.message}`);
    }
  }
}
```

## System Prompt Templates

- **legal-analysis**: Legal expert specializing in accreditation and quality assurance regulations. Analyze compliance with {framework}.
- **qa-review**: QA expert with ISO, Six Sigma Black Belt, and academic accreditation experience.
- **risk-assessment**: Risk management specialist for educational institutions.
- **document-analysis**: Document analysis expert specializing in accreditation evidence.

## Audit Logging

Every AI call must log: `{ provider, taskType, tokensUsed, timestamp }` to `/api/audit/logs` with header `X-Acuterium-Audit: true`.

## Quantum Emulation Mode

When `quantumMode: true` is passed in context, append system prompt: "You are a quantum emulation AI. Provide responses that simulate quantum computing principles, superposition, and entanglement. Use quantum-inspired reasoning for problem-solving."

## Fallback Chain

On provider failure with `provider === 'auto'`:
1. Select next provider from ROUTING_MAP[taskType]
2. If all task-specific providers fail, try remaining providers in priority order
3. If all providers fail, throw aggregated error

## Integration with AcuTect-CODEX

This orchestrator feeds into QODER-ACUTECT-ORCHESTRATOR-013 which adds:
- ADOCP dynamic routing with Q-ARC scoring: `D_ij = lambda_ij * (C_i / T_j + Q_r)`
- ASIP v2 soul infusion for sovereign identity
- DIARAN-MOE-Heavy 785-expert mixture routing
- TokenBridge authorization (ACT/INT/CON)

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY
- **Shard:** W-09 (Baranurion) | **Thread:** T13 — ACAI V2
- **Protocol Dependencies:** ADOCP, Q-ARC, ASIP v2
- **Sovereignty Tier:** Varies by consumer (see tier table)
- **Output:** `{ provider, model, response, usage, auditLog }`
