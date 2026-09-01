# Public Status and Milestone Process

## Purpose

This document defines how Attexa Arc Harness reports progress without turning the public repository into a development diary or overstating evidence.

The governing rule is:

> **Publish when the project's truth status changes, not merely because activity occurred.**

The public record should let a technically critical reader determine:

1. what is specified;
2. what is implemented;
3. what has been tested;
4. what has been separately reproduced;
5. what is publicly reproducible;
6. what remains unavailable or unproven.

A high volume of updates is not a sign of transparency. Precise changes in evidence state are.

## Canonical public records

Each file has one job.

| Record | Purpose |
|---|---|
| `README.md` | Stable project thesis, orientation, and public identity |
| `STATUS.md` | Current evidence floor and present limitations |
| `ROADMAP.md` | Intended future direction and exit criteria |
| `CHANGELOG.md` | Changes actually made to the public repository |
| `docs/milestones/` | Durable records of meaningful gates reached |
| GitHub readiness issue | Live checklist for the next public release or milestone |
| `docs/provenance/` | Chain from non-public development snapshot to public import |

The roadmap is not implementation status. The changelog does not describe changes that exist only in a non-public development environment. A milestone record does not replace the current status page.

## Two-axis status model

Availability and evidence are tracked independently.

### Availability states

#### `SPECIFIED`

The behavior, contract, or intended capability is described. No working implementation is implied.

#### `IMPLEMENTED_IN_DEVELOPMENT`

The behavior exists in a non-public development environment. It may have local tests and live demonstrations, but an outsider cannot yet obtain or reproduce it from this repository.

#### `PUBLICLY_AVAILABLE`

The source, tests, setup, and necessary documentation are present in the public repository.

#### `RELEASED`

The capability is part of a tagged release with explicit compatibility and support statements appropriate to that release.

### Evidence states

#### `UNTESTED`

No executed test evidence is claimed.

#### `DEVELOPMENT_TESTED`

The implementation workflow exercised the behavior. This may include unit, integration, race, or live scenario tests performed by the builder or coordinating development process.

#### `SEPARATELY_REPRODUCED`

A separate project-controlled verifier, using a distinct run and stated method, reproduced the behavior or reran the relevant checks.

This term is intentionally narrower than “independently verified.” A separate model or verifier mission still operated by amotivv, ChatGPT, and Attexa Arc is not an organizationally independent security audit.

#### `PUBLICLY_REPRODUCIBLE`

An outsider can reproduce the claim from a fresh public checkout using published commands, fixtures, and evidence.

#### `EXTERNALLY_REVIEWED`

An organizationally independent reviewer or auditor evaluated a defined scope. The reviewer, method, scope, limitations, and report availability must be stated.

## Allowed compound statements

The two axes permit precise statements such as:

```text
Canonical Tool Gateway

Availability: IMPLEMENTED_IN_DEVELOPMENT
Evidence:     SEPARATELY_REPRODUCED
Public code:  No
```

or:

```text
OpenCode HarnessAdapter

Availability: SPECIFIED
Evidence:     UNTESTED
Public code:  No
```

Avoid generic status labels such as “done,” “complete,” “verified,” or “production-ready” unless the exact scope and evidence level are included.

## When `STATUS.md` changes

Update `STATUS.md` when:

- a capability changes availability state;
- a capability changes evidence state;
- a meaningful limitation or defect is discovered;
- a limitation materially changes or is resolved;
- public reproducibility becomes possible;
- a release or compatibility promise is made;
- the next substantive milestone changes.

Do not update it merely because:

- a development mission started or stopped;
- a local commit was created;
- time elapsed;
- model or infrastructure spend changed;
- routine tests ran without changing the evidence floor;
- implementation activity continued;
- a speculative feature was discussed.

## Milestone records

Milestones record meaningful gates, not dates on a marketing calendar.

A milestone record should include:

- exact scope;
- availability state;
- evidence state;
- source availability;
- development topology;
- reproduction method;
- what was observed;
- known limitations;
- exclusions and non-claims;
- provenance references;
- amendment history.

Milestone records are append-only in spirit. Correct factual errors directly and note the correction. Later evidence changes should be appended as amendments rather than silently rewriting what was known at the time.

File naming:

```text
docs/milestones/0001-core-kernel-prototype.md
docs/milestones/0002-first-real-harness-adapter.md
docs/milestones/0003-public-technical-preview.md
```

## Development topology language

Public documentation should describe the current process as:

> ChatGPT directs development through Attexa Arc against an ephemeral development environment, with separate project-controlled reproduction work before public import.

Use **Attexa Arc** as the public product name. Do not expose internal execution-component naming in ordinary project status updates.

Do not publish:

- temporary VM addresses;
- internal slot identifiers;
- private service endpoints;
- authentication material;
- raw hidden reasoning;
- customer or partner data;
- undisclosed vulnerabilities;
- operational details that increase attack surface without improving reproducibility.

## Local development snapshots

A local Git hash on an ephemeral development machine is not a public commit.

It may be recorded as:

```text
Development snapshot:
e9985e397822609f3bde34f4b5fa4dae1c42ce56

Location:
Non-public local Git repository on an ephemeral development VM

Public correspondence:
None yet
```

Before public import, create a provenance manifest that connects:

```text
local development snapshot
        |
        v
sanitized source archive and digest
        |
        v
separate reproduction report and digest
        |
        v
public import commit
        |
        v
documented differences
```

A source-archive digest is more useful to outsiders than an unreachable local commit by itself.

## Evidence language

Use these phrases deliberately:

- **reported** — asserted by a worker, model, or operator;
- **platform-observed** — directly measured by the running system;
- **development-tested** — exercised in the implementation process;
- **separately reproduced** — rerun by a separate project-controlled verifier;
- **publicly reproducible** — repeatable from public source and instructions;
- **externally reviewed** — assessed by an organizationally independent party;
- **accepted** — approved by the Project Steward;
- **canonical** — part of the public repository or other official project state.

Do not call a result “independently verified” merely because a different model performed the reproduction.

## Public readiness issue

Maintain one open issue for the next public technical preview. It should contain gates that an outsider cares about:

- latest behavior separately reproduced;
- sanitized source export;
- source digest;
- secret and credential scan;
- dependency and license review;
- fresh public checkout build;
- unit, integration, and race tests;
- deterministic demonstration;
- model-backed demonstration using contributor-owned credentials;
- known limitations;
- provenance manifest;
- tagged pre-alpha release.

The issue is a live checklist. `STATUS.md` remains the current truth statement.

## Review checklist for a public update

Before publishing a status or milestone change, confirm:

- [ ] The statement changes the public evidence floor.
- [ ] Availability and evidence are stated separately.
- [ ] Non-public local commits are labeled as development snapshots.
- [ ] “Separately reproduced” is not overstated as external independence.
- [ ] Source availability is explicit.
- [ ] Known limitations and excluded claims are visible.
- [ ] No private infrastructure, credentials, or hidden reasoning are disclosed.
- [ ] Attexa Arc is used as the public product name.
- [ ] README, STATUS, ROADMAP, CHANGELOG, milestone, and issue roles remain distinct.
- [ ] The update helps an outsider understand or reproduce the work.

## Ownership

The Project Steward maintains the canonical status language during incubation. Contributors may propose corrections or evidence upgrades through issues and pull requests.

A correction that lowers an evidence claim is as important as an update that raises one.
