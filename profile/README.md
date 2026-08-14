<p align="center">
  <img src="ainfera-mark-ice.svg" alt="Studio Tune" width="140" />
</p>

<h1 align="center">Studio Tune</h1>

<p align="center">
  <strong>The agent-native workspace for building, adapting, and evaluating AI systems.</strong>
</p>

<p align="center">
  Built by Ainfera · evidence before claims
</p>

<p align="center">
  <a href="https://studiotune.ai"><img alt="Website" src="https://img.shields.io/badge/studiotune.ai-0B1220?style=for-the-badge&labelColor=111A2E" /></a>
  &nbsp;
  <a href="https://github.com/studiotune-ai"><img alt="GitHub" src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" /></a>
</p>

---

```text
intent → inspect → plan → approve → adapt → evaluate → verify
```

## What we are building

Studio Tune is a local-first, evidence-first workspace for people who want to build and adapt AI systems without losing track of what actually changed.

The product is designed around a simple principle:

> Build from your data. See what changed. Know whether it should advance.

Studio Tune is the new product direction from Ainfera. The legal and corporate transition, if any, is separate from this product profile and is not being claimed here.

## Product surfaces

| Surface | Role | Current posture |
|:--|:--|:--|
| **Studio Tune Desktop** | Local desktop workflow for intent, planning, bounded runs, comparison, evidence, and verification | Private pre-release development |
| **Studio Tune CLI** | Scriptable and continuous-integration surface for the same lifecycle | Beta-track boundary |
| **Tune Agent** | Constrained local agent that proposes safe actions and reports verified results | Contract-validation boundary |
| **StudioTune OS** | Operating system for agent-native company workflows, policies, evidence, and bounded execution | Private foundation |

## Evidence loop

```text
intent
  → inspect
  → bounded plan
  → human approval
  → controlled run
  → parent / candidate comparison
  → failure diff
  → evidence packet
  → offline verification
  → SHIP / HOLD / REVISE / REJECT
```

A completed run is not proof of improvement.

A green workflow is not permission to publish or deploy.

If the evidence chain is incomplete, the system holds.

## Current implementation boundary

Implemented and tested locally:

- Bounded local lifecycle mechanics
- Parent/candidate comparison and failure-diff mechanics
- Evidence packets and offline verification
- Typed desktop IPC boundary
- Builder journey over the local socket
- Constrained agent-contract validation

Not claimed:

- Real QLoRA training
- Real model inference in the evaluation path
- NVIDIA, remote, or GPU execution
- Production readiness
- Autonomous publication or deployment
- Independent certification or accreditation
- Customer, revenue, benchmark, or superiority claims

The current repositories report their own exact test evidence and claim ceilings.

## Operating principles

- Local first.
- Evidence before claims.
- Human approval at consequential boundaries.
- Agents propose and execute within bounded authority.
- Refusal is a valid result.
- Personal founder context does not enter public product surfaces.
- Hermes remains the control-plane runtime for agent operations.

## Repositories

- [`desktop-app`](https://github.com/studiotune-ai/desktop-app) — Studio Tune Desktop
- [`cli`](https://github.com/studiotune-ai/cli) — Studio Tune CLI
- [`tune-agent`](https://github.com/studiotune-ai/tune-agent) — constrained Tune Agent boundary
- [`studiotune-os`](https://github.com/studiotune-ai/studiotune-os) — private company operating-system foundation

## Public status

Studio Tune is in private pre-release development.

The profile describes the product direction and verified mechanics. It does not announce a completed company rename, public release, production deployment, or commercial availability.

---

<sub>Studio Tune · Built by Ainfera · Evidence before claims</sub>
