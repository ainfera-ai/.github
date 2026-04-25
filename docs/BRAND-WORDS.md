# Ainfera · BRAND-WORDS.md

**Version:** 2026-04-25 · reconciled with Brand Identity v1.1 LOCK
**Owner:** brand
**Enforcement:** every rule below has a grep command. Every grep has
an expected hit count. Run all greps before every push. Any mismatch
between expected and actual is a blocker.

This document is **not prose**. Treat each rule as a unit test against
the codebase. If a rule says "expect 0 hits," 0 means 0 — not "few"
or "mostly clean."

This document supersedes any prior `docs/BRAND-WORDS.md` in the repo.
If a prose-style version exists, replace it with this file.

---

## §1 · Required strings (these MUST appear)

These exact strings appear on the public site (`ainfera.ai`). Do not
paraphrase. Do not embellish.

### §1.1 Hero headline

```
The infrastructure exchange for the agentic economy
```

Verify:

```bash
grep -F "The infrastructure exchange for the agentic economy" src/
# Expected: ≥ 1 hit (homepage hero)
```

### §1.2 Hero sub-copy

```
The neutral trust and settlement layer for the agentic economy — five integrated layers: Agent Trust Score, Sandboxed Compute, Metered Billing & Settlement, Agent Identity & Registry, and Multi-Protocol Orchestration.
```

Verify:

```bash
grep -F "neutral trust and settlement layer for the agentic economy" src/
# Expected: ≥ 1 hit
```

### §1.3 Billboard / secondary tagline

```
The infrastructure for intelligence.
```

Verify:

```bash
grep -F "The infrastructure for intelligence" src/
# Expected: ≥ 1 hit if used; 0 if not used (acceptable either way)
```

### §1.4 Copyright line (footer)

```
© 2026 Ainfera
```

Verify:

```bash
grep -F "© 2026 Ainfera" src/
# Expected: ≥ 1 hit
grep -F "© 2026 Ainfera Pte" src/
# Expected: 0 hits (Pte. Ltd. retired, see §3.3)
```

---

## §2 · Canonical technical values

### §2.1 Five-layer architecture

| #  | Full name                       | Short form    |
|----|--------------------------------|---------------|
| 1  | Agent Trust Score (ATS)         | Trust         |
| 2  | Sandboxed Compute               | Compute       |
| 3  | Metered Billing & Settlement    | Settlement    |
| 4  | Agent Identity & Registry       | **Registry**  |
| 5  | Multi-Protocol Orchestration    | Orchestration |

**"Discovery" as a layer name is RETIRED.** Folded into Registry.

Verify:

```bash
grep -rEn "\bDiscovery\b" src/ public/
# Expected: 0 hits in user-facing code paths

grep -rEn "Identity\b(?!.*Registry)" src/ public/
# Expected: 0 hits where "Identity" appears WITHOUT "Registry" as
# the layer-4 short form
```

### §2.2 ATS dimensions

```
Safety, Reliability, Quality, Performance, Reputation
```

- Scale: 0–1000
- Aggregation: geometric mean (any 0 collapses total)
- Letter grades: CCC, BBB, BB, A, AA, AAA

Verify:

```bash
grep -rEin "cost.efficiency|cost_efficiency" src/
# Expected: 0 hits

grep -rEn "Compliance" src/ public/
# Expected: 0 hits in ATS scoring contexts; manual review

grep -rEn "\bSecurity\b" src/ public/
# Acceptable in general security contexts; flag if used as ATS dim
```

### §2.3 Agent DID format

```
did:web:ainfera.ai:agents:{id}
```

Verify:

```bash
grep -rEn "did:ainfera" src/ public/ docs/
# Expected: 0 hits

grep -rEn "did:web:ainfera\.ai:agents:" src/ public/
# Expected: ≥ 1 hit if any DID example shown
```

### §2.4 Revenue split

```
85 / 5 / 10
```

(creator / platform / compute)

Verify:

```bash
grep -rEn "60/25/15|60 / 25 / 15" .
# Expected: 0 hits

grep -rEn "3-5%|3 to 5%" src/ public/
# Expected: 0 hits
```

### §2.5 Package install + import

| Package | Install                   | Import                            |
|---------|---------------------------|-----------------------------------|
| CLI     | `pip install ainfera`     | `ainfera` (CLI command)           |
| SDK     | `pip install ainfera-sdk` | `from ainfera_sdk import Ainfera` |

Verify:

```bash
grep -rEn "from ainfera import|from ainfera\." . --include="*.md" --include="*.tsx" --include="*.ts" --include="*.jsx" --include="*.js"
# Expected: 0 hits in marketing content
# In SDK source itself, `from ainfera_sdk.<sub>` is fine
```

### §2.6 Domains

| Host             | Role                              |
|------------------|-----------------------------------|
| `ainfera.ai`     | Public site                       |
| `app.ainfera.ai` | Authenticated console             |
| `api.ainfera.ai` | Platform API + OpenAPI reference  |

```bash
grep -rEn "console\.ainfera\.ai" src/ public/
# Expected: 0 hits
```

### §2.7 Public contact

```
hello@ainfera.ai
security@ainfera.ai     (vulnerability disclosure only)
```

```bash
grep -rEn "@ainfera\." src/ public/ | grep -v "hello@ainfera\.ai" | grep -v "security@ainfera\.ai"
# Expected: 0 hits except in lawyer-reviewed legal docs
```

---

## §3 · Forbidden strings (these MUST NOT appear)

Each subsection has a single grep. Every one must return 0 hits in
user-facing paths.

### §3.1 Named third parties

```bash
grep -rEin "\b(nvidia|nim|nemo|guardrails|stripe|adyen|paid\.ai|skyfire|nekuda|airwallex|mercury|anthropic|claude(?! code)|langchain|langgraph|crewai|autogen|llamaindex|google ?adk|openai|hugging ?face|mistral|llama|gemini|deepseek|docker|gvisor|firecracker|kubernetes|aws|gcp|azure|cloudflare|vercel|railway|opentelemetry|prometheus|grafana|clickhouse|kafka|redis|temporal|nyse|smu|ntu|nus|y combinator|antler|inception)\b" src/ public/ --include="*.tsx" --include="*.ts" --include="*.jsx" --include="*.js" --include="*.mdx" --include="*.md"
# Expected: 0 hits
```

**Exception 1:** SDK package `pyproject.toml` may list framework
adapter extras (`langchain`, `crewai`) in
`[project.optional-dependencies]`. README may reference these in a
"Technical dependencies" section near the bottom. Nowhere else.

**Exception 2:** Operational config files (Helm values, K8s manifests,
Dockerfile base images) may name services by config-format necessity.
Confined to those file types only.

**Exception 3:** Open standards by name are NOT third parties:
`MCP`, `A2A`, `W3C DID`, `did:web`, `OAuth`, `JWT`, `HTTPS`, `TCP`,
`JSON`, `Apache 2.0` (license name).

### §3.2 Funding, stage, availability, timeline

```bash
grep -rEin "\b(seed|series [abc]|pre-?seed|mega-?seed|safe(?! and)|mfn|valuation|cap table|round|raise|bridge|tranche|private beta|public beta|early access|alpha|\bbeta\b|\bGA\b|general availability|coming soon|coming Q[0-9]|arriving|roadmap|stage [0-9]|phase [0-9]|deprecated|preview|experimental|Q[1-4] 20[0-9]{2}|H[12] 20[0-9]{2}|\bM[0-9]+\b|ARR|MRR)\b" src/ public/ --include="*.tsx" --include="*.ts" --include="*.jsx" --include="*.js" --include="*.mdx" --include="*.md"
# Expected: 0 hits
```

### §3.3 Entity domicile + legal framing

```bash
grep -rEin "\b(pte\.? ?ltd|pty ?ltd|inc\.|llc|gmbh|\bsa\b|\bbv\b|\bag\b|\bsingapore\b|\bsg\b|republic of singapore|delaware|united states|\beu\b|\buk\b|pdpa|mas|acra|iras|\bgst\b|\bcpf\b|gdpr|\bsec\b|finra|\bfca\b|bafin)\b" src/ public/ --include="*.tsx" --include="*.ts" --include="*.jsx" --include="*.js" --include="*.mdx" --include="*.md"
# Expected: 0 hits
```

Exception: lawyer-reviewed `/terms` and `/privacy` pages may contain
jurisdictional language. Marketing pages, product copy, READMEs may not.

### §3.4 Founder identity

```bash
grep -rEin "\b(hizrian|izzy|raz)\b" src/ public/ docs/ --include="*.tsx" --include="*.ts" --include="*.jsx" --include="*.js" --include="*.mdx" --include="*.md" --include="*.json" --include="*.yml" --include="*.yaml"
# Expected: 0 hits
```

**Exception:** Git commit author/committer fields are EXEMPT from
this rule per founder decision 2026-04-25. Author = `Hizrian Raz
<hizrian@ainfera.ai>`. See §6 for full rationale and scope.

### §3.5 Forbidden technical terms

```bash
grep -rEin "\b(blockchain|crypto|stablecoin|web3|x402|mainnet|hash chain|merkle|decentralized|wallet|smart contract|mining|coin)\b" src/ public/ --include="*.tsx" --include="*.ts" --include="*.jsx" --include="*.js" --include="*.mdx" --include="*.md"
# Expected: 0 hits
```

`token` and `ledger` need context-specific review:

```bash
grep -rEin "\btoken\b" src/ public/
# Acceptable: auth/JWT/OAuth tokens
# NOT acceptable: financial tokens — manual review

grep -rEin "\bledger\b" src/ public/
# Acceptable: internal variable names in private modules
# NOT acceptable: user-facing copy describing settlement
```

### §3.6 Retired entity names

```bash
grep -rEn "\b(Agentium|Delaware)\b" src/ public/ docs/
# Expected: 0 hits
```

### §3.7 Retired phrasing

```bash
grep -F "Infrastructure, not intelligence." src/ public/
# Expected: 0 hits (positions against AI — retired)

grep -F "NYSE of the agentic economy" src/ public/
# Expected: 0 hits (names external institution — retired)

grep -F "designed to be boring on purpose" src/ public/
# Expected: 0 hits (older variant — retired)

grep -F "AI agent economy" src/ public/
# Expected: 0 hits (canonical is "agentic economy")
```

---

## §4 · Voice rules

These are not greppable. Manual review.

1. **Company voice only.** No "I built this" / "we believe" framing
   that implies named individuals.
2. **Present tense.** What the product does today. No "we used to" /
   "we will" / "we plan to" / "coming soon."
3. **Functional, not ceremonial.** No mission statements, no
   manifestos, no origin stories on public surfaces.
4. **No institutional name-dropping.** No "working with X" / "backed
   by X" / "inspired by X."
5. **Boring on purpose.** Infrastructure language, not SaaS language.

---

## §5 · Landing page composition

The home page (`ainfera.ai/`) has six sections IN THIS ORDER. No
others.

| § | Section          | Purpose                                                              |
|---|------------------|----------------------------------------------------------------------|
| 1 | Hero             | What is this — answers "is this for me" in two seconds              |
| 2 | Bring your agent | Whatever you built runs here — single code block proof              |
| 3 | What you get     | Five layers as five problem-solution rows                            |
| 4 | Neutrality       | Three concrete commitments: portable identity, open code, fiat payouts |
| 5 | Get started      | Single install command + docs link + sign in                         |
| 6 | Footer           | Minimal — entity, two emails, links                                  |

Sections that MUST NOT appear:
- Logo wall of partner integrations
- "Trusted by" customer grid
- Pricing tiers (Free/Pro/Enterprise)
- Roadmap / "what's next"
- Founder bio / team section
- Stage badges (private beta, etc.)
- Compliance badges (SOC 2, etc.)
- Newsletter signup
- Social proof metrics

---

## §6 · Git author identity (constitutional override — DOCUMENTED EXCEPTION)

**Decision 2026-04-25:** Git author fields use the founder's real
identity across ALL repos, public and private:

```bash
git config user.name "Hizrian Raz"
git config user.email "hizrian@ainfera.ai"
```

### Why this is documented as an exception

A previous repo-level `CLAUDE.md` policy stated:

> Commit author identity is configured at the repo level. Do not
> attribute commits to any individual contributor.

That policy is OVERRIDDEN by this section, scoped narrowly:

| Field | Identity |
|---|---|
| Git author (commit metadata) | `Hizrian Raz <hizrian@ainfera.ai>` ✓ |
| Git committer (commit metadata) | `Hizrian Raz <hizrian@ainfera.ai>` ✓ |
| README contributor section | NOT PRESENT — anonymity rule still applies |
| `pyproject.toml` author/maintainer (PyPI metadata) | `Ainfera <hello@ainfera.ai>` — anonymity still applies |
| `package.json` author | `Ainfera <hello@ainfera.ai>` — anonymity still applies |
| Code comments / docstring authorship | NOT PRESENT — anonymity rule still applies |
| Profile / about pages | NOT PRESENT — anonymity rule still applies |
| GitHub org settings | `Ainfera`, no founder name |

**The override is git-author-only.** Every other anonymity rule
continues to apply.

### Verification

```bash
git log -1 --format=fuller
# Author: Hizrian Raz <hizrian@ainfera.ai>
# Commit: Hizrian Raz <hizrian@ainfera.ai>
```

If a repo's own `CLAUDE.md` contradicts this section, this section
wins. Update the repo's `CLAUDE.md` to point at this document
(`docs/BRAND-WORDS.md §6`) rather than maintain a separate policy.

---

## §7 · Enforcement protocol

Before every `git push`:

1. Run every grep in §1 — verify required strings present
2. Run every grep in §2 — verify canonical values consistent
3. Run every grep in §3 — verify forbidden strings absent (0 hits)
4. Manual voice review per §4
5. If any grep returns unexpected count → fix before push
6. Document any grep exception in PR description with rationale

This document supersedes any prior copy guideline. If
`docs/BRAND-WORDS.md` and another doc disagree, this document wins.
Update this document first if canonical changes.
