# Installing the Acuterium Marketplace into Claude Code

This repository is now an **installable Claude Code plugin marketplace**. That means
any Claude Code session — local CLI, Claude Code on the web, or mobile — can pull in
the Acuterium doctrines and skills instead of them sitting inert on disk.

> **Why this matters:** Claude Code only auto-loads skills/agents/doctrines that are
> *installed* (via a marketplace) or physically present in a folder's `.claude/`
> directory. Simply having this repo cloned nearby is not enough — it must be added
> as a marketplace and its plugins installed. That is what these steps do.

## What's included

| Plugin | Skills | Contents |
| ------ | ------ | -------- |
| `acuterium-doctrines` | 19 | Sovereign doctrines/protocols: ADOCP routing, ASIP soul-infusion, BARANURION-governed engines, PRISM, RED-TEAM 8-gate QA, MADA briefing, DAG engine, LLM judge/matrix/negotiation, CrewAI executor, task-recovery, Erebus cyber-defence, threat/strategy/RIA/URANA/PSI/ENC/CASCADE engines. |
| `acuterium-legal-ai` | 5 | RUZN.AI legal: contract review, legal research, document drafting, due diligence, e-discovery (Omani/GCC standards). |
| `acuterium-compliance-ai` | 5 | Compliance monitoring, regulatory-change intelligence, policy enforcement, risk assessment, compliance workflow automation. |
| `acuterium-audit-ai` | 3 | Internal audit automation, automated compliance auditing, audit-trail & evidence management. |
| `acuterium-quality-assurance` | 3 | Ūrānā QMS: QA framework, accreditation/attestation intelligence, CAPA narrative generation. |

Install any subset with `/plugin install <name>@acuterium-skills-marketplace`.

**Next tranche (not yet packaged):** the ~2,206 technical/infra skills under
`registry/skills/wagha/` (Azure, Terraform, CrewAI, CI/CD, etc.) can be added as a
bulk `acuterium-registry` plugin in a follow-up.

## Install (from GitHub — works on local, web, and mobile)

In any Claude Code session:

```
/plugin marketplace add acuterium-technologies/acuterium-skills-marketplace
/plugin install acuterium-doctrines@acuterium-skills-marketplace
/reload-plugins
```

Once installed at user scope, the doctrines are available in **every** session,
including inside `C:\Acuterium_Seeker_Crews`. Claude will auto-invoke a doctrine
when a task matches its description (e.g. a routing task pulls in `adocp-routing-protocol`),
or you can call one explicitly:

```
/acuterium-doctrines:adocp-routing-protocol
```

## Install from a local clone (offline / air-gapped)

If the repo is cloned on the machine (e.g. under `C:\` or your Seeker Crews tree),
point the marketplace at the local path instead:

```
/plugin marketplace add C:\path\to\acuterium-skills-marketplace
/plugin install acuterium-doctrines@acuterium-skills-marketplace
/reload-plugins
```

## Updating

After new doctrines/plugins are pushed to this repo:

```
/plugin marketplace update acuterium-skills-marketplace
```

## Wiring it into the Seeker Crews handoff

Add this line to the top of your kickoff prompt (or to `HANDOFF.md` §5 Setup) so the
executing session always has the doctrines loaded before it plans the crew:

> Before executing, ensure the Acuterium doctrines are installed:
> `/plugin marketplace add acuterium-technologies/acuterium-skills-marketplace` then
> `/plugin install acuterium-doctrines@acuterium-skills-marketplace` and `/reload-plugins`.
> Use ADOCP for task-to-model routing and RED-TEAM 8-gate QA before declaring any task done.
