# Milestone 0002: Real OpenCode Adapter and Concurrent Builder/Reviewer Run

**Status:** Reached  
**Availability:** `IMPLEMENTED_IN_DEVELOPMENT`  
**Evidence:** `SEPARATELY_REPRODUCED` for the scope below, including a fresh separate project-controlled rerun  
**Public source:** No  
**Recorded:** September 1, 2026

## Meaning of this milestone

This milestone records that the private, single-node Go/SQLite Arc Harness Kernel reference prototype crossed the design-only boundary for its first real downstream harness integration: a real OpenCode `HarnessAdapter` operating simultaneous sandboxed Builder and Reviewer child loops through Arc, with distinct tool and inference authority, isolated state, and parent reconciliation.

It does **not** mark a public technical preview, publicly reproducible source, a stable interface, a production deployment, or an external security review or certification.

## Development arrangement

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
local Git repository, arcd service, SQLite state, tests
```

The implementation exists in a non-public local Git repository on the ephemeral VM. The public GitHub repository contains the architecture and project process, but not the runnable kernel source at the time of this record.

## Scope demonstrated

Building on Milestone 0001, this milestone adds:

- a real OpenCode 1.18.25 `HarnessAdapter`, distinct from the `RuntimeDriver`, running native OpenCode Builder and Reviewer processes under Arc-mediated inference authority, Arc-mediated tool authority, and operating-system isolation;
- two simultaneous sandboxed OpenCode child loops, Builder and Reviewer, with independent capability bundles, workspace views, event streams, and Outcomes;
- parent reconciliation of the resulting child Outcomes and a compare-and-set Commit;
- durable Address and Canon generations, the Commission → Work → Attempt → Outcome → Commit lifecycle, the canonical Tool Gateway, and the MCP bridge, all exercised again in this run;
- equivalent-work reuse and stale-generation conflict handling;
- persistence across a service restart;
- explicit cancellation cascade and cancelled-parent terminal-state integrity, corrected and exercised in this run.

## Reproduction method

The original OpenCode Builder/Reviewer run measured wall-clock overlap between the two child processes. A separate, project-controlled fresh rerun of the same scope from a clean state reproduced the concurrent-execution behavior and rechecked the full scope above through fresh test, race, and conformance checks.

As internal prototype evidence rather than a benchmark claim:

- original run: **43.630 seconds** of measured overlap between the two simultaneous OpenCode child processes;
- fresh separate rerun: **34.881 seconds** of measured overlap.

Both figures are single-node, single-run timings from a private development environment. They support the claim that two real child harness processes genuinely overlapped in execution. They are not a throughput, latency, or scale benchmark, and no production performance claim is made from them.

The fresh rerun additionally reported all twelve internal verification groups as passing:

1. Address and Canon durability
2. Commission → Work → Attempt → Outcome → Commit lifecycle
3. Canonical Tool Gateway
4. MCP bridge
5. Real model-backed tool-use loops
6. `RuntimeDriver` / `HarnessAdapter` separation
7. Concurrent Parent and Child Work
8. Real OpenCode Builder/Reviewer run
9. Parent reconciliation
10. Compare-and-set Commit
11. Equivalent-work reuse and stale-generation conflict handling
12. Restart persistence and cancellation semantics

This was a **separate, project-controlled reproduction**, not an organizationally independent audit or certification.

## Known limitations

- The source was not available in the public repository.
- The implementation is single-node and uses Go, SQLite, and local artifact storage.
- Public installation and clean-room reproduction were not possible.
- The measured overlap figures are single-run, single-node timings, not a benchmark suite.
- Production security, availability, disaster recovery, and operational support were not evaluated.
- The separate reproduction was project-controlled, not a third-party review.

## Explicit non-claims

This milestone does not claim:

- that the implementation source is already public;
- that the result is reproducible from this repository;
- that the system is production-ready, highly available, or disaster-recoverable;
- that the system has been externally audited or certified;
- that the system is ready for unattended consequential actions;
- that all worker or runtime isolation boundaries are unbreakable;
- that model output is semantically correct;
- that the local Git history is public provenance.

## Next gate

The next public gate is to import and sanitize the reference implementation, make it reproducible from the public repository, publish conformance fixtures and evidence, and obtain reproduction from public source.

## Amendments

No amendments at initial publication.
