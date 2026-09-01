# Project Status

_Last materially updated: September 1, 2026_

## Current state

**Pre-alpha. Architecture public; implementation not yet publicly reproducible.**

The Attexa Arc Harness architecture, governance, interoperability direction, and public development process are available in this repository.

A working Go/SQLite implementation of the Arc Harness Kernel currently exists in a non-public local Git repository on an ephemeral DigitalOcean development VM. ChatGPT is directing development through **Attexa Arc**, which coordinates implementation and separate reproduction work against that environment. The runnable kernel source has not yet been imported into this public repository.

The following core behavior has been exercised and separately reproduced within the project:

- durable Addresses and Canon generations;
- the Commission → Work → Attempt → Outcome → Commit lifecycle;
- real OpenRouter-backed agent tool-use loops;
- per-Attempt inference and tool authority;
- the canonical Tool Gateway and MCP bridge;
- the runtime-neutral `HarnessAdapter` contract;
- concurrent Parent and Child Work with distinct Builder and Reviewer capabilities;
- independent child artifacts, events, and Outcomes;
- parent reconciliation and compare-and-set Commit;
- equivalent-work reuse and stale-generation conflict handling;
- persistence across service restart.

The latest local development snapshot, `e9985e397822609f3bde34f4b5fa4dae1c42ce56`, reportedly corrects two cancellation defects by making cascade behavior explicit and preventing a cancelled parent from later being rewritten as successful. Those corrections passed development tests and live scenarios. A separate Claude Sonnet reproduction is still in progress, so the cancellation corrections remain **development-tested**, not yet **separately reproduced**.

The first real OpenCode `HarnessAdapter` and a run with two simultaneous sandboxed OpenCode child loops have not yet been completed.

No claim of production readiness, high availability, disaster recovery, external security review, or stable public interfaces is being made.

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
| Runtime-neutral `HarnessAdapter` contract | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | Architecture only |
| Concurrent Parent and Child Work | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Builder and Reviewer capability separation | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Parent reconciliation and CAS Commit | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Equivalent-work reuse | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Stale-generation conflict | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Service-restart persistence | `IMPLEMENTED_IN_DEVELOPMENT` | `SEPARATELY_REPRODUCED` | No |
| Explicit cancellation cascade | `IMPLEMENTED_IN_DEVELOPMENT` | `DEVELOPMENT_TESTED` | No |
| Cancelled-parent terminal-state integrity | `IMPLEMENTED_IN_DEVELOPMENT` | `DEVELOPMENT_TESTED` | No |
| Real OpenCode `HarnessAdapter` | `SPECIFIED` | `UNTESTED` | No |
| Two simultaneous sandboxed OpenCode child loops | `SPECIFIED` | `UNTESTED` | No |
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

- [Milestone 0001: Core Kernel Prototype](docs/milestones/0001-core-kernel-prototype.md) — reached in a non-public development environment; core behavior separately reproduced; latest cancellation amendment still under separate reproduction.
- **Next:** first real OpenCode adapter and two simultaneous sandboxed OpenCode child loops.
- **Then:** sanitized, evidence-bearing public technical preview.

## Next public truth-state change

The next update to this file should occur when one of these happens:

1. the latest cancellation corrections are separately reproduced;
2. the real OpenCode adapter and concurrent OpenCode run reach a stated evidence level;
3. a material limitation or defect changes the current evidence floor;
4. sanitized source becomes publicly reproducible;
5. a tagged release or compatibility promise is made.

Routine local commits, mission starts, elapsed time, model spend, and ordinary implementation activity are intentionally not published as project-status changes.
