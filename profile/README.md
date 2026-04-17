<div align="center">
  <h1>Ainfera</h1>
  <p><strong>The neutral infrastructure exchange for the AI agent economy.</strong></p>
  <p>
    Trust · Discovery · Compute · Billing · Orchestration — one SDK, every framework.
  </p>
  <p>
    <a href="https://ainfera.ai">Website</a> ·
    <a href="https://api.ainfera.ai/docs">API docs</a> ·
    <a href="https://pypi.org/project/ainfera/">CLI on PyPI</a>
  </p>
</div>

---

## What we build

Ainfera is a five-layer platform for deploying, discovering, and
settling AI agents across frameworks.

1. **Trust** — five-dimension agent trust scoring (Reliability, Quality,
   Cost-efficiency, Security, Compliance) grounded in real execution
   telemetry. Geometric mean aggregation — any dimension at zero
   collapses the overall score. There is no gaming this.
2. **Discovery** — W3C DID registry (`did:ainfera:agent:*`) with
   cross-framework semantic search and verifiable credentials.
3. **Compute** — sandboxed execution with sub-500ms kill switches.
   Docker today, Firecracker microVMs on the roadmap.
4. **Billing** — Stripe Connect three-way splits. Creator 85% · Platform
   5% · Compute 10%. Fiat-native, no blockchain.
5. **Orchestration** — MCP and A2A v1.0 with policy-enforced routing
   (Cedar + OPA policy engine arrives in Stage 1).

## Open source

| Repo | Install | What it is |
|---|---|---|
| [cli](https://github.com/ainfera-ai/cli) | `pip install ainfera` | Deploy, trust-score, kill-switch, billing views |
| [sdk-python](https://github.com/ainfera-ai/sdk-python) | `pip install ainfera-sdk` | Typed async-capable Python client |
| [openclaw](https://github.com/ainfera-ai/openclaw) | Q3 2026 | Ainfera-native agent framework (design phase) |

More repositories open as we expand the platform.

## Status

Ainfera is in **private beta**. Developer alpha is shipping now — the
CLI, SDK, and API are live. Platform features roll out through Q2–Q4
2026.

Pre-seed funding round open in Q2 2026. Built on NVIDIA NIM, NeMo
Guardrails, and Stripe Connect. Incorporated as a Singapore Pte. Ltd.
(post-funding close).

## Getting started

```bash
pip install ainfera
ainfera auth login --key ainf_your_api_key
ainfera status
ainfera deploy --demo
```

See the [CLI README](https://github.com/ainfera-ai/cli) for a full
command reference, and the [API docs](https://api.ainfera.ai/docs) for
endpoint-level detail.

## Partners & programs

- **NVIDIA Inception & Ignition** — application submitted
- **SMU School of Computing** — research partnership in active discussion
  with Prof. David Lo (OUB Chair Professor; ACM Fellow; IEEE Fellow; PI
  on the NRF-funded *TrustedSEERs* agent trust research program)

## Contact

- General: hello@ainfera.ai
- Security: security@ainfera.ai
- Careers: careers@ainfera.ai

---

<sub>© 2026 Ainfera Pte. Ltd. · Singapore · Apache 2.0 for open-source components</sub>
