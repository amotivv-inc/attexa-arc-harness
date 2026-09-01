# Attexa Arc Harness

**A durable work harness for temporary intelligence.**

Attexa Arc Harness is an open-source framework for operating agentic work across models, runtimes, tools, people, and time.

Its core, the **Arc Harness Kernel**, makes the work, not the agent session, the durable object:

```text
Address → Situation → Commission → Work → Attempt → Outcome → Commit → Accretion
```

The model may change. The inner harness may change. The runtime may change. The worker may disappear. **The work remains.**

## Project status

> **Pre-alpha. Architecture public; implementation not yet publicly reproducible.**

This repository contains the project definition, architecture, governance, interoperability direction, and public development process.

A working Go/SQLite implementation of `arcd` exists in a non-public development environment and has exercised the core Address-to-Commit lifecycle, real model-backed tool loops, per-Attempt authority, the Tool Gateway and MCP bridge, and concurrent Parent and Child Work. Core behavior has been separately reproduced within the project, but the runnable kernel source has not yet been imported here.

Read [STATUS.md](STATUS.md) for the current evidence floor, [the first milestone record](docs/milestones/0001-core-kernel-prototype.md) for the scope already demonstrated, [ROADMAP.md](ROADMAP.md) for intended next work, and [SECURITY.md](SECURITY.md) for responsible disclosure.

The current implementation should not yet be relied upon for production security, availability, disaster recovery, or unattended consequential actions.

## The problem

Most agent frameworks begin with the worker:

```text
Here is an agent.
Give it tools, memory, and a task.
```

Arc begins with the work:

```text
Here is a durable, governed workplace.
Commission the right temporary intelligence into it
under the right context, authority, and limits.
```

A model context window is temporary. A chat is temporary. A process, container, VM, and coding harness are temporary. Organizations still need the files, decisions, permissions, evidence, unfinished work, and accumulated understanding to survive all of them.

## The core model

| Object | Purpose |
|---|---|
| **Address** | Durable identity and contract boundary for a body of work |
| **Situation** | Current, versioned, minimum-sufficient view compiled for a need |
| **Commission** | Desired outcome, quality bar, authority, disclosure, time, and cost ceilings |
| **Work** | Durable undertaking that survives individual execution attempts |
| **Attempt** | One bounded execution episode using a selected runtime and performer |
| **Outcome** | Structured artifacts, claims, observations, tests, limitations, and proposals |
| **Commit** | The only path that makes an official state change or consequential effect |
| **Accretion** | Scoped, provenance-aware knowledge that makes later work better or cheaper |

```text
                         ATTEXA ARC HARNESS

Principal
    |
    v
Address ──compile──> Situation ──commission──> Durable Work
                                                    |
                              +---------------------+---------------------+
                              |                                           |
                              v                                           v
                         Attempt A                                   Attempt B
                    Runtime + Harness                           Human / Agent / Service
                              |                                           |
                              +---------------------+---------------------+
                                                    |
                                                    v
                                      Outcome + Candidate knowledge
                                                    |
                                             explicit Commit
                                                    |
                                                    v
                                         New Canon generation
                                                    |
                                                    v
                                         Better next Situation
```

## Outer harness, not inner harness

OpenCode, Codex, Claude Code, and custom model workers contain their own reasoning and tool-use loops. Arc does not replace those loops. It governs them from outside:

- what durable Work they are serving;
- which Situation and artifacts they receive;
- which exact tools, models, data, and budgets are available;
- how ambiguity becomes a durable Decision Request rather than a guess;
- how progress, artifacts, claims, and effects are observed;
- what survives when a worker exits or fails;
- what requires verification or human judgment;
- what may cross the Commit boundary into official state.

Execution is composed from two independent adapter types:

```text
Attempt
  ├── RuntimeDriver    where and how execution runs
  └── HarnessAdapter   which inner agent or human workflow runs there
```

This allows combinations such as a local process with the reference worker, a container with Codex, or an Attexa Arc execution environment with OpenCode without changing Arc's durable Work model.

## Architectural commitments

The project is being built around several non-negotiable principles:

1. **The Address is durable; the worker is temporary.**
2. **Situation is compiled, not inherited as an ever-growing transcript.**
3. **Work survives retries, replacement workers, model changes, and verification attempts.**
4. **Capabilities replace ambient provider credentials.**
5. **Worker claims remain distinct from platform observations and independent verification.**
6. **Only Commit changes canonical state.**
7. **Write-ahead intent precedes effecting operations.**
8. **Ambiguous external effects are reconciled before retry.**
9. **No model, runtime, tool, disclosure route, or authority silently falls back.**
10. **Reuse is checked before spending more inference or human attention.**
11. **Large results become artifacts; context is paged, checkpointed, and rotated.**
12. **Parallel workers do not share uncontrolled mutable state.**

Read [ARCHITECTURE.md](ARCHITECTURE.md) for the current system model.

## What Arc is not

Arc is not presented as:

- a universal VM or sandbox containment solution;
- an assertion that any hypervisor or worker is unbreakable;
- a replacement for an inner coding-agent harness;
- a prompt-template collection or multi-agent role-play library;
- a memory database that treats persistence as truth;
- a proprietary client stub whose meaningful semantics exist only in a hosted service.

The open project is intended to contain the real single-node kernel semantics, local runtime, contracts, adapters, and conformance tests. Managed Attexa Arc is the supported workplace, infrastructure, integration, governance, and trust-service product built around it.

## Arc Practice

A durable workplace does not become coherent merely because its files persist. **Arc Practice** is the open discipline of establishing and stewarding a body of work so its purpose, accepted state, evidence, authority, unresolved uncertainty, and ability to continue survive changes in people, agents, vendors, and tools.

An **Arc Practitioner** helps bring this method to a real body of work. Their success is measured not by how much process they create, but by whether another qualified person or agent can enter the workplace, understand its current Situation, and continue useful Work without depending on the practitioner's private memory.

An **Arc Steward** maintains an established workplace over time.

No Attexa Certified Arc Practitioner program is currently offered. Any future credential should require an end-to-end assessed practicum and a successful continuity handoff, not merely course completion or familiarity with Arc terminology.

See:

- [Arc Practice](docs/practice/README.md)
- [Arc Practitioner Charter](docs/practice/ARC-PRACTITIONER-CHARTER.md)
- [Continuity Handoff Test](docs/practice/CONTINUITY-HANDOFF-TEST.md)
- [The Work Should Remain thesis series](docs/thesis/README.md)

## Building Arc with Arc

The project will use its own concepts to advance itself. Public development evidence may include:

- the Commission and Outcome Contract for a bounded change;
- implementation and verifier Attempts;
- produced patches and artifact digests;
- test and conformance results;
- Decision Requests and accepted architectural decisions;
- release manifests and evidence bundles.

It will not include private chain-of-thought, credentials, customer data, undisclosed vulnerabilities, or performative transcript dumps.

See:

- [Building Arc with Arc](docs/BUILDING-IN-PUBLIC.md)
- [Public status and milestone process](docs/STATUS-UPDATES.md)
- [Milestone records](docs/milestones/README.md)
- [Public import provenance](docs/provenance/README.md)

## Planned repository shape

```text
cmd/             arcd, arc CLI, bridges, and operator utilities
kernel/          durable state machines and control logic
contracts/       versioned schemas and interoperability contracts
runtime/         RuntimeDriver implementations
harness/         HarnessAdapter implementations
toolplane/       capability-aware tool gateway and frontends
inference/       model-provider gateway and adapters
evidence/        truth classes, receipts, and verifier interfaces
conformance/     portable adapter and kernel tests
examples/        deterministic and model-backed examples
docs/            architecture and operating documentation
rfcs/            public design proposals and decisions
```

The exact code layout may evolve before the first technical preview. The object model and invariants should change only through an explicit public architecture decision.

## Contributing

The project welcomes implementation, specification, testing, security, documentation, adapter, and use-case contributions from people and AI-assisted workflows.

Begin with [CONTRIBUTING.md](CONTRIBUTING.md), follow the [Code of Conduct](CODE_OF_CONDUCT.md), and use the RFC process for changes to durable semantics or interoperability contracts.

## License and trademarks

The source and documentation in this repository are licensed under the [Apache License 2.0](LICENSE).

The license does not grant rights to use amotivv or Attexa names and marks beyond reasonable attribution. See [TRADEMARKS.md](TRADEMARKS.md).

## Project relationship

```text
Attexa Arc Harness     open-source project and distribution
Arc Harness Kernel     core architecture implemented by arcd
arcd                   reference daemon
arc                    command-line and operator interface
Attexa Arc             managed workplace and commercial product
```

Attexa Arc Harness was initiated by **amotivv, inc.**
