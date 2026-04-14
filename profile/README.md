# Ainfera

**The unified infrastructure platform for the AI agent economy.**

Trust scoring · Sandboxed compute · Metered billing · Kill switches · Agent identity

---

## What is Ainfera?

Ainfera is the neutral exchange layer for AI agents — the infrastructure that handles trust, execution, billing, and identity so agent builders can focus on building. Think of us as the NYSE of the agentic economy: we don't build agents, we make every agent trustworthy, billable, and killable.

### Core Platform Layers

| Layer | What it does |
|-------|-------------|
| **Agent Trust Score (ATS)** | Composite 0–1000 scoring across Safety, Reliability, Quality, Performance, and Reputation. Geometric mean — zero in any dimension means zero overall. |
| **Sandboxed Compute** | Docker containers (v0.1) → Firecracker microVMs (v1.0). Sub-125ms boot, full isolation, resource limits. |
| **Metered Billing** | Hash-chained PostgreSQL ledger with SHA-256 tamper evidence. Three-way revenue split via Stripe Connect. |
| **Agent Identity** | W3C DIDs and Verifiable Credentials. Persistent cryptographic identity for every agent. |
| **Multi-Protocol Orchestration** | MCP and A2A protocol support. Connect agents to tools and to each other. |

## Platform

| Service | URL | Status |
|---------|-----|--------|
| **API** | [api.ainfera.ai](https://api.ainfera.ai/docs) | ![API Status](https://img.shields.io/badge/status-live-brightgreen) |
| **Console** | [console.ainfera.ai](https://console.ainfera.ai) | ![Console Status](https://img.shields.io/badge/status-live-brightgreen) |
| **CLI** | `pip install ainfera` | ![PyPI](https://img.shields.io/pypi/v/ainfera) |
| **SDK** | `pip install ainfera-sdk` | Coming soon |

## Repositories

| Repo | Description | Stack |
|------|-------------|-------|
| [`platform-api`](https://github.com/ainfera-ai/platform-api) | FastAPI backend — trust scoring, billing, execution, registry | Python, FastAPI, PostgreSQL, Redis |
| [`console`](https://github.com/ainfera-ai/console) | Web dashboard — agent management, trust visualization, playground | Next.js 15, TypeScript, Tailwind |
| [`cli`](https://github.com/ainfera-ai/cli) | Command-line interface — deploy agents from your terminal | Python, Click, Rich |
| [`sdk-python`](https://github.com/ainfera-ai/sdk-python) | Python SDK — programmatic access to the Ainfera API | Python, httpx, Pydantic |
| [`infra`](https://github.com/ainfera-ai/infra) | Infrastructure-as-code — Docker Compose, Terraform, K8s | Docker, Terraform, Kustomize |
| [`sandbox-runtime`](https://github.com/ainfera-ai/sandbox-runtime) | Agent sandbox execution runtime | Python, Docker, Firecracker |

## Quick Start

```bash
# Install the CLI
pip install ainfera

# Check platform status
ainfera health

# Initialize an agent project
ainfera init --name my-agent --framework langchain

# Deploy your agent
ainfera deploy
```

## Trust Scoring

Every agent on Ainfera receives a trust score across 6 dimensions:

```
┌─────────────────────────────────────────┐
│  AAA  │  912  │  support-bot            │
│  AA   │  847  │  research-agent         │
│  A    │  721  │  data-analyst           │
│  BBB  │  654  │  code-reviewer          │
│  B    │  452  │  deploy-bot             │
│  CCC  │  312  │  rogue-bot  ⚠ KILLED   │
└─────────────────────────────────────────┘
```

Scores use **geometric mean** — zero in any dimension collapses the total score. No gaming, no hiding behind one strong metric.

## Architecture

```
Agent Builder → ainfera deploy → Ainfera Platform
                                    ├── Trust Score Engine (6 dimensions)
                                    ├── Sandboxed Execution (Docker/Firecracker)
                                    ├── Metered Billing (hash-chained ledger)
                                    ├── Kill Switch (Redis, <500ms)
                                    └── Inference Proxy (OpenAI, NIM)
```

## Company

**Ainfera**

We're building the trust and settlement infrastructure for the AI agent economy.

- 🌐 [ainfera.ai](https://ainfera.ai)
- 📧 hello@ainfera.ai
- 🐦 [@ainfera](https://twitter.com/ainfera)

---

*Ainfera — Trust infrastructure for the AI agent economy.*
