# Milestone 0001: Core Kernel Prototype

**Status:** Reached  
**Availability:** `IMPLEMENTED_IN_DEVELOPMENT`  
**Evidence:** `SEPARATELY_REPRODUCED` for the core scope below  
**Public source:** No  
**Recorded:** September 1, 2026

## Meaning of this milestone

This milestone records that the Arc Harness Kernel progressed beyond a paper architecture into a working, deployed single-node prototype whose central durable-work behavior was exercised and separately reproduced within the project.

It does **not** mark a public technical preview, a stable interface, a production deployment, an external security review, or completion of the first real downstream harness integration.

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

The implementation exists in a non-public local Git repository on the ephemeral VM. Attexa Arc coordinates implementation and separate project-controlled reproduction runs. The public GitHub repository contains the architecture and project process, but not the runnable kernel source at the time of this record.

## Scope demonstrated

The stated core scope includes:

- durable Addresses and Canon generations;
- Commission, Work, Attempt, Outcome, Candidate, and Commit records;
- compare-and-set Canon advancement;
- stale-generation conflict without overwrite;
- equivalent-work reuse;
- persistence across service restart;
- a real OpenRouter-backed model and typed tool-use loop;
- per-Attempt inference authority;
- per-Attempt tool authority;
- canonical Tool Gateway behavior;
- MCP bridge behavior;
- a runtime-neutral `HarnessAdapter` contract and reference foundation;
- concurrent Parent and Child Work;
- distinct Builder and Reviewer capabilities;
- separate child artifacts, event streams, and Outcomes;
- parent comparison and reconciliation before Commit;
- bounded cancellation and non-canonical working state.

## Reproduction method

A separate Claude Sonnet verifier run, coordinated through Attexa Arc, connected to the development environment and reproduced the stated core behaviors by inspecting the live deployment, rerunning relevant checks, and exercising representative scenarios.

This was a **separate project-controlled reproduction**, not an organizationally independent audit or certification.

## Current development snapshot

At the time this milestone was recorded, the latest reported local development snapshot was:

```text
e9985e397822609f3bde34f4b5fa4dae1c42ce56
```

This is a local Git identifier from the ephemeral development environment. It is not a commit in `amotivv-inc/attexa-arc-harness` and has no public source correspondence yet.

## Cancellation amendment in progress

Development after the separately reproduced core baseline identified two cancellation defects:

1. cascade behavior was not exposed explicitly enough;
2. a cancelled parent could later be rewritten as successful.

The current local development snapshot reportedly corrects both defects. Full tests, race tests, and live cancellation/restart scenarios passed in the development workflow.

A separate reproduction of those corrections was still in progress when this milestone was recorded. Therefore:

```text
Explicit cancellation cascade:
  IMPLEMENTED_IN_DEVELOPMENT / DEVELOPMENT_TESTED

Cancelled-parent terminal-state integrity:
  IMPLEMENTED_IN_DEVELOPMENT / DEVELOPMENT_TESTED
```

Those two corrections are not included in this record's `SEPARATELY_REPRODUCED` claim until an amendment says otherwise.

## Known limitations

- The source was not available in the public repository.
- The implementation was single-node and used Go, SQLite, and local artifact storage.
- Public installation and clean-room reproduction were not possible.
- The real OpenCode `HarnessAdapter` had not been completed.
- Two simultaneous sandboxed OpenCode child loops had not been run through Arc.
- Automatic Attempt rotation and complete adaptive context compaction were not implemented.
- First-class fork and merge operations were not implemented.
- Standing Commissions were not implemented.
- Production security, availability, disaster recovery, and operational support were not evaluated.
- The separate reproduction was project-controlled, not a third-party review.

## Explicit non-claims

This milestone does not claim:

- that the system is production-ready;
- that all worker or runtime isolation boundaries are unbreakable;
- that model output is semantically correct;
- that every current local change has been separately reproduced;
- that the local Git history is public provenance;
- that the public repository can yet execute the kernel;
- that OpenCode, Codex, or Claude Code has been integrated as a real downstream harness.

## Next gate

The next substantive milestone is:

> **A real OpenCode `HarnessAdapter` operating two simultaneous sandboxed Builder and Reviewer child loops through Arc, with distinct tool and inference authority, isolated state, parent reconciliation, and a reproducible evidence bundle.**

After that, the project will prepare a sanitized public source import and evidence-bearing `v0.1.0-alpha` technical preview.

## Amendments

**September 1, 2026:** The cancellation corrections described above under “Cancellation amendment in progress” have since been separately reproduced, and the next gate described above has been reached. See [Milestone 0002: Real OpenCode Adapter and Concurrent Builder/Reviewer Run](0002-real-opencode-adapter-and-concurrent-run.md) and the current [STATUS.md](../../STATUS.md) for the updated evidence floor. The scope and findings recorded above for Milestone 0001 at the time of initial publication are otherwise unchanged.
