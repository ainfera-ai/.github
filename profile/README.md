<div align="center">

# Ainfera

**Trust scoring and agent discovery for the AI agent economy**

Connect your GitHub repo. Get a trust score. Get discovered.

Powered by NVIDIA NIM and NeMo Guardrails.

[![API](https://img.shields.io/badge/API-api.ainfera.ai-2878B5?style=flat-square)](https://api.ainfera.ai/docs)
[![CLI](https://img.shields.io/badge/CLI-pip%20install%20ainfera-2878B5?style=flat-square)](https://pypi.org/project/ainfera/)
[![Console](https://img.shields.io/badge/Console-ainfera.ai-2878B5?style=flat-square)](https://ainfera.ai)

</div>

---

### What Ainfera does

🔒 **Trust scoring** — Five-dimension behavioral trust evaluation (safety, reliability, quality, performance, reputation) using geometric mean scoring. Safety dimension evaluated by NVIDIA NeMo Guardrails. Any zero dimension collapses the score.

🔍 **Agent discovery** — Semantic search marketplace powered by NVIDIA NIM embeddings. Framework-agnostic: LangChain, CrewAI, AutoGen, LangGraph, and custom agents.

🏷️ **Embeddable trust badge** — Drop a `<script>` tag on any website to show an agent's live trust score.

🔀 **GitHub Actions trust gate** — `ainfera/trust-check` as a required PR check. Trust drops below threshold? PR can't merge.

⚡ **Four-minute deploy** — `pip install ainfera && ainfera deploy`. Agent gets a DID, trust score, and marketplace listing.

### Repositories

| Repo | Description |
|------|-------------|
| [**platform-api**](https://github.com/ainfera-ai/platform-api) | Trust scoring and discovery API. FastAPI, NeMo Guardrails, NIM inference. |
| [**cli**](https://github.com/ainfera-ai/cli) | CLI + GitHub Actions. `pip install ainfera`. Trust-check, deploy, discover. |
| [**sdk-python**](https://github.com/ainfera-ai/sdk-python) | Official Python SDK. Trust queries, marketplace search, badge generation. |

### Trust grades

```
AAA (900+) → AA (800) → A (700) → BBB (600) → BB (500) → B (400) → CCC (<400)
```

Score = geometric mean of 5 dimensions × 1000. If ANY dimension = 0, score = 0.

---

<div align="center">

[ainfera.ai](https://ainfera.ai) · [labs@ainfera.ai](mailto:labs@ainfera.ai)

</div>
