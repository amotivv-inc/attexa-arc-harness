# Project Status

_Last materially updated: September 1, 2026_

## Current state

**Pre-alpha / technical-preview preparation; not production-ready.**

The Attexa Arc Harness architecture, governance, interoperability direction, and public development process are available in this repository and under active development.

A separate, private, single-node Go/SQLite Arc Harness Kernel reference prototype has crossed the design-only boundary: it runs, and its core behavior has been separately reproduced within the project. The prototype currently exists in a non-public local Git repository on an ephemeral DigitalOcean development VM. ChatGPT is directing development through **Attexa Arc**, which coordinates implementation and separate reproduction work against that environment. The runnable kernel source has not yet been imported into this public repository.

The following core behavior has been exercised and separately reproduced within the project:

- durable Addresses and Canon generations;
- the Commission → Work → Attempt → Outcome → Commit lifecycle;
- real OpenRouter-backed agent tool-use loops;
- per-Attempt inference and tool authority;
- the canonical Tool Gateway and MCP bridge;
- the runtime-neutral `RuntimeDriver` / `HarnessAdapter` separation;
- concurrent Parent and Child Work with distinct Builder and Reviewer capabilities;
- a real OpenCode 1.18.25 `HarnessAdapter` running Builder and Reviewer child processes under Arc-mediated inference authority, Arc-mediated tool authority, and operating-system isolation;
- separate child artifacts, events, and Outcomes;
- parent reconciliation and compare-and-set Commit;
- equivalent-work reuse and stale-generation conflict handling;
- persistence across service restart;
- explicit cancellation cascade and cancelled-parent terminal-state integrity.

A fresh, separate project-controlled rerun reproduced the full scope above from a clean state. It reported all twelve internal verification groups as passing under fresh test, race, and conformance checks: Address and Canon durability; the Commission-to-Commit lifecycle; the Tool Gateway; the MCP bridge; model-backed loops; the `RuntimeDriver` / `HarnessAdapter` separation; concurrent Parent and Child Work; the OpenCode Builder/Reviewer run; reconciliation; compare-and-set Commit; reuse and stale-conflict handling; and restart persistence with cancellation semantics.

As internal prototype evidence rather than a benchmark claim, the original simultaneous OpenCode Builder/Reviewer run measured **43.630 seconds** of wall-clock overlap between the two child processes; the fresh separate rerun measured **34.881 seconds** of overlap. Both observations are single-node, single-run timings from a private development environment. They support the claim that two real child harness processes genuinely overlapped in execution; they are not a performance benchmark and say nothing about production throughput, latency, or scale.

This milestone does **not** mean that the implementation source is already public, that it is reproducible from this repository, that it is production-ready, highly available, or disaster-recoverable, that it has been externally audited or certified, or that it is ready for unattended consequential actions. No claim of production readiness, high availability, disaster recovery, external security review, or stable public interfaces is being made.

The next public gate is to import and sanitize the reference implementation, make it reproducible from the public repository, publish conformance fixtures and evidence, and obtain reproduction from public source.

## How to read this page

Project status is tracked on two independent axes.

### Availability

| State | Meaning |
|---|---|
| `SPECIFIED` | The behavior or contract is described publicly, but a working implementation is not claimed. |
| `IMPLEMENTED_IN_DEVELOPMENT` | It exists in the non-public development environment. |
| `PUBLICLY_AVAILABLE` | Source, tests, and setup are present in this repository. |
| `RELEASED` | It is included in a tagged release with stated compatibility expectations. |

### Evidence

| State | Meaning |
|---|---|
| `UNTESTED` | No executed test evidence is claimed. |
| `DEVELOPMENT_TESTED` | The implementation team exercised the behavior. |
| `SEPARATELY_REPRODUCED` | A separate project-controlled verifier reran or reproduced the behavior. This is not a third-party audit. |
| `PUBLICLY_REPRODUCIBLE` | An outsider can reproduce the claim from the public repository and published instructions. |
| `EXTERNALLY_REVIEWED` | An organizationally independent reviewer or auditor evaluated the stated scope. |

See [docs/STATUS-UPDATES.md](docs/STATUS-UPDATES.md) for the complete update process and language rules.

## Capability evidence floor

| Capability | Availability | Evidence | Publicly runnable here |
|---|---|---|---|
| Address and Canon | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No; architecture only |
| Commission → Work → Attempt → Outcome → Commit | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No; architecture only |
| Real model-backed tool-use loop | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Per-Attempt inference authority | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Per-Attempt tool authority | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Canonical Tool Gateway | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| MCP bridge | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Runtime-neutral `RuntimeDriver` / `HarnessAdapter` separation | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | Architecture only |
| Concurrent Parent and Child Work | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Builder and Reviewer capability separation | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Real OpenCode 1.18.25 `HarnessAdapter` | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Two simultaneous sandboxed OpenCode Builder/Reviewer child loops | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Parent reconciliation and CAS Commit | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Equivalent-work reuse | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Stale-generation conflict | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Service-restart persistence | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Explicit cancellation cascade | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Cancelled-parent terminal-state integrity | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Automatic Attempt rotation before context exhaustion | `SPECIFIED` | `UNTESTED` | No |
| Public technical preview | `SPECIFIED` | `UNTESTED` | No |
| Production resilience | Not claimed | Not evaluated | No |

## Current development topology

```text
Project steward
      |
      v
ChatGPT
planning, commissioning, steering, and review
      |
      v
Attexa Arc
durable coordination and separate verifier work
      |
      v
Ephemeral DigitalOcean development VM
local Git history, running arcd, SQLite state, tests
      |
      +-- implementation work
      +-- live model-backed demonstrations
      +-- separate reproduction work
      +-- sanitized source and evidence exports
      |
      v
Public import review
      |
      v
github.com/amotivv-inc/attexa-arc-harness
```

Local development commit identifiers are provenance references only. They are not public GitHub commits, releases, or reproducibility claims.

## Milestones

- [Milestone 0001: Core Kernel Prototype](docs/milestones/0001-core-kernel-prototype.md) — reached in a non-public development environment; core behavior separately reproduced.
- [Milestone 0002: Real OpenCode Adapter and Concurrent Builder/Reviewer Run](docs/milestones/0002-real-opencode-adapter-and-concurrent-run.md) — reached in the same non-public development environment; a real OpenCode 1.18.25 `HarnessAdapter` ran simultaneous sandboxed Builder and Reviewer child loops, and the full scope was separately reproduced in a fresh project-controlled rerun across all internal verification groups.
- **Next:** import and sanitize the reference implementation, make it reproducible from the public repository, publish conformance fixtures and evidence, and obtain reproduction from public source.
- **Then:** sanitized, evidence-bearing public technical preview.

## Next public truth-state change

The next update to this file should occur when one of these happens:

1. the sanitized reference implementation becomes reproducible from the public repository;
2. published conformance fixtures and evidence become available;
3. an outsider reproduces the implementation from public source;
4. a material limitation or defect changes the current evidence floor;
5. a tagged release or compatibility promise is made.

Routine local commits, mission starts, elapsed time, model spend, and ordinary implementation activity are intentionally not published as project-status changes.
