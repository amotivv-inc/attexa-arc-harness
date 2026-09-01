# Architecture

## Definition

The **Arc Harness Kernel** is a runtime-neutral outer harness for durable, governed work. It coordinates temporary performers without making any one model, chat, process, VM, or inner agent harness the owner of the work.

The defining statement is:

> **The workplace persists. Intelligence visits.**

The kernel does not prescribe how an inner agent reasons. It defines how a temporary performer enters a durable body of work, receives current context and bounded authority, produces observable results, and leaves the workplace in a state that another performer can accurately continue.

## The abstraction tower

```text
┌──────────────────────────────────────────────────────────────┐
│ Surfaces                                                     │
│ Agent Anything | CLI | API | Snowflake | customer systems    │
├──────────────────────────────────────────────────────────────┤
│ Agent-facing Arc operations                                  │
│ resolve | commission | observe | control | commit             │
├──────────────────────────────────────────────────────────────┤
│ Arc Harness Kernel                                           │
│ Address | Situation | Work graph | Outcome | Commit           │
│ context | authority | recovery | accretion | evidence         │
├──────────────────────────────────────────────────────────────┤
│ Capability planes                                            │
│ Tool Gateway | Inference Gateway | Policy | Evidence          │
├──────────────────────────────────────────────────────────────┤
│ Execution adapters                                           │
│ RuntimeDriver + HarnessAdapter + HumanTaskAdapter             │
├──────────────────────────────────────────────────────────────┤
│ Substrates                                                   │
│ process | container | VM | storage | model and tool providers │
└──────────────────────────────────────────────────────────────┘
```

Each layer can evolve behind stable contracts. Infrastructure details remain available for diagnosis, but normal agents operate through the durable work vocabulary.

## The core object model

```text
Principal
    |
    v
Address
    |
    | compile for the current need
    v
Situation
    |
    | desired result and ceilings
    v
Commission
    |
    | create, reuse, or no-op
    v
Work
    |
    +-- Attempt 1
    +-- Attempt 2
    +-- verification Attempt
    |
    v
Outcome + Candidates
    |
    | explicit official transition
    v
Commit
    |
    v
New Canon generation and better next Situation
```

### Principal

A human, service, organization, scheduled authority, or delegated agent that may request Work, answer Decision Requests, approve actions, or manage recurring authority according to policy.

### Address

The durable identity and contract boundary of a body of work. An Address contains or references purpose, owner, invariants, Canon schema, policy, capability, evidence, accretion, and placement profiles.

An Address is not one physical machine or one disk.

### Situation

A current, versioned, policy-filtered, minimum-sufficient view compiled for a specific need. Situation is derived from durable state; it is not a transcript and is not whatever the previous model happened to summarize.

### Commission

The desired outcome and ceilings for Work. It states objective, quality bar, deliverables, stop conditions, verification target, authority, disclosure, time, and cost limits. It does not require the caller to choose hosts, slots, credentials, or provider-specific recipes.

### Work

The durable undertaking. Work owns objective, dependencies, parent and child relationships, Attempts, events, Decision Requests, checkpoints, accounting, Outcomes, Candidates, and reconciliation state.

### Attempt

One bounded execution episode. An Attempt binds a Situation, internal Plan, Lease, runtime, performer, exact inference route, capability bundle, workspace view, event stream, resource envelope, checkpoints, and terminal result.

### Outcome

A structured result that separates artifacts, worker claims, platform observations, tests, independent verification, unresolved questions, limitations, resource use, Candidate knowledge, and recommended next moves.

### Commit

The only path that changes canonical state or records an accepted consequential effect. Commit validates generation, policy, approval, authority, effect reconciliation, evidence, and compare-and-set before advancing Canon.

### Accretion

Scoped, provenance-aware reusable state produced from completed Work. Initial Candidate types include assertions, decisions, procedures, artifacts, open questions, negative results, and benchmark summaries.

## Address state planes

```text
Agentic Address
  |
  +-- Manifest
  |     identity, purpose, invariants, contract references
  |
  +-- Canon
  |     official accepted state
  |
  +-- Workspaces
  |     durable exploratory and private working state
  |
  +-- Artifact Store
  |     immutable or content-addressed retained bytes
  |
  +-- Candidate Queue
  |     quarantined proposed reusable knowledge
  |
  +-- Ledger and Evidence Graph
        authority, events, provenance, receipts, verification
```

Persistence is not acceptance. A file may survive for years without being canonical. Only Commit changes Canon.

## Version dimensions

Arc separates several forms of versioning:

- **Address generation** changes when Canon or a load-bearing Address contract changes.
- **Situation revision** changes when the derived current view changes.
- **Working revision** changes as durable exploratory work evolves.
- **Policy version** identifies the authority semantics applied to planning and execution.
- **Ledger head** identifies the latest durable control or evidence event.
- **Toolset digest** binds the exact tool catalog granted to an Attempt.
- **Context digest** binds the selected inputs and summaries used by an Attempt.

Commit uses compare-and-set against an expected Address generation. A stale Commit returns a typed conflict rather than overwriting newer state.

## Situation and context economy

Arc prevents context exhaustion by architecture, not by replaying the entire history into a larger model window.

```text
Durable Address state
        |
        v
Context Compiler
        |
        +-- compact Situation Header
        +-- exact objective and authority
        +-- relevant Canon
        +-- active Work and conflicts
        +-- fresh artifacts and evidence
        +-- applicable procedures
        +-- relevant negative results
        +-- unresolved questions
        +-- on-demand references
        |
        v
Bounded Attempt context
```

Every compilation should produce a Context Manifest containing source object versions, inclusion reasons, freshness, token and byte estimates, generated summaries, policy-safe omission categories, and on-demand indexes.

Large tool results become content-addressed artifacts. The model receives a bounded summary and may retrieve relevant sections when needed. Before context compaction or Attempt rotation, the performer creates a structured checkpoint containing completed work, conclusions, assumptions, unresolved questions, artifact references, external effects, and remaining work.

The intended invariant is:

> **Continuity is preserved without requiring one model context to carry the continuity.**

## Runtime and harness composition

Arc separates where execution runs from which inner loop runs there.

```text
Attempt
  |
  +-- RuntimeDriver
  |     process, container, Attexa Arc execution environment,
  |     confidential runtime, remote service, or another substrate
  |
  +-- HarnessAdapter
        reference worker, OpenCode, Codex, Claude Code,
        or another agent harness
```

A `RuntimeDriver` controls process or VM lifecycle, filesystem projection, network posture, operating-system enforcement, cancellation, checkpointing, resource observation, and cleanup.

A `HarnessAdapter` renders native configuration, model endpoint settings, MCP or plugin registration, launch arguments, event normalization, steering, checkpoint semantics, and result extraction.

The separation avoids pairwise implementations tied to one runtime and one harness. Runtime and harness adapters are composed independently.

## Human and deterministic performers

Not every Attempt is an AI process.

```text
Attempt
   |
   v
Performer
   |
   +-- Agent performer
   |     RuntimeDriver + HarnessAdapter
   |
   +-- Human performer
   |     HumanTaskAdapter + verified Principal
   |
   +-- Deterministic performer
         fixed service or procedure
```

A Human Performer can supply domain judgment through a typed, signed Outcome. For Verified Actions, this can realize a domain-attestation requirement without conflating judgment, authorization, execution, evidence, and Canon acceptance.

## Inference plane

Upstream model credentials stay outside the worker where the selected harness permits it.

```text
Inner harness
    |
    | Attempt-scoped local inference token
    v
Arc Inference Gateway
    |
    +-- OpenRouter
    +-- OpenAI
    +-- Anthropic
    +-- confidential inference
    +-- local inference
```

The gateway enforces exact model selection, no silent fallback, cancellation, timeout, turn/token/cost ceilings, request and response digests, provider request IDs, usage accounting, retries, and finish reasons.

## Tool plane

Harness-native MCP, plugin, SDK, or CLI interfaces are projections of one canonical Arc Tool Contract.

A tool definition includes stable ID and version, input and output schemas, side-effect class, required scopes, parameter and path constraints, idempotency, approval policy, timeout, data exposure, resource hints, evidence level, and synchronous or durable asynchronous operation mode.

```text
Harness
   |
   | Attempt-scoped capability
   v
Arc Tool Gateway
   |
   +-- filtered discovery
   +-- schema and scope validation
   +-- parameter and path constraints
   +-- budget and expiration
   +-- write-ahead intent
   +-- idempotency and reconciliation
   +-- artifact-backed large results
   +-- normalized evidence
   |
   v
Tool and action providers
```

The worker receives an Arc capability, not a GitHub token, cloud key, database password, or other durable provider credential.

Harness configuration improves compatibility and ergonomics. It is not the security boundary. Authority is enforced by the RuntimeDriver, Tool Gateway, Inference Gateway, policy evaluation, and Commit path.

## Tool classes

Arc distinguishes:

1. **Runtime-native capabilities**, such as filesystem operations, compilers, and local tests. These are primarily enforced by the RuntimeDriver and operating system.
2. **Brokered service tools**, such as GitHub, research, data platforms, email, or cloud APIs. These execute through the Tool Gateway or provider plane.
3. **Consequential transitions**, such as merge, deploy, publish, send, modify production data, or approve a payment. The performer normally proposes these; Arc resolves policy, approval, narrow authority, execution, reconciliation, evidence, and Commit.

Long operations should be durable and asynchronous through start, observe, collect, and cancel operations rather than holding one inference turn open.

## Tool-use and continuous execution

An inner harness may repeatedly alternate between model calls and typed tools within one bounded Attempt.

```text
model turn
    |
    v
typed tool request
    |
    v
validate capability, schema, scope, path, budget, state
    |
    v
record intent → execute → record result
    |
    v
bounded result returned to harness
    |
    +-----------------------> next model turn
```

One Attempt may run unattended until completion, a blocking Decision Request, cancellation, a resource limit, policy refusal, provider failure, or checkpoint boundary.

Long-running Work should continue through checkpointed replacement Attempts rather than one immortal process or context:

```text
Durable Work
   +-- Attempt 1 → checkpoint
   +-- Attempt 2 → continue from fresh compiled context
   +-- Attempt 3 → independent verification or reconciliation
```

Recurring operation should use Standing Commissions that compile fresh Situation and choose reuse, no-op, or new Work for each occurrence. A Standing Commission is finite standing authority, not a permanent worker.

## Parallel Work

A Parent Work may commission isolated Child Works:

```text
Parent Work
   |
   +-- Builder Child
   |     writable overlay, builder tool lease, own artifacts
   |
   +-- Reviewer Child
         read-only base, reviewer tool lease, own artifacts
```

Each child has independent Attempts, budgets, capability bundles, toolset digests, event cursors, workspace views, Outcomes, Candidates, and cancellation state.

Children return immutable artifacts and structured Outcomes. The parent compares agreements, disagreements, verification status, and proposed deltas. Reconciliation is not an automatic merge. Only Commit may promote selected results.

## Decision Requests

A performer creates a durable Decision Request rather than guessing through material ambiguity. The request states the question, reason, choices, blocking status, timeout, policy-defined safe default if one exists, cost of waiting, and related Work.

No declared safe default means block. A performer cannot invent its own default, and an answer cannot silently widen authority.

## Truth and evidence

Arc keeps evidence sources distinct:

```text
reported
platform_observed
self_tested
independently_verified
externally_reconciled
operator_accepted
canonical
```

A result is not independently verified merely because the same worker wrote and ran a test. Verification requires a verifier identity, method, scope, result, limitations, and evidence reference.

The Ledger and evidence graph should be queryable by Address, Work, Attempt, model, runtime, tool invocation, artifact, Outcome claim, Candidate, Commit, and external effect.

## Commit

Commit is the sole official mutation and consequential-effect path:

```text
write-ahead intent
      |
schema and generation validation
      |
policy and approval
      |
narrow capability
      |
effect execution
      |
reconciliation
      |
receipt and evidence
      |
Canon compare-and-set
```

An ambiguous external effect is reconciled before retry. A stale generation is rejected without mutation.

## Core invariants

An implementation is Arc only if it preserves these invariants:

1. The Address is the durable locus of work.
2. Situation is compiled, not inherited as narrative.
3. Commission states desired result and ceilings.
4. Work survives Attempts.
5. Only Commit changes Canon.
6. Authority remains outside the worker.
7. Agent testimony is not proof.
8. Write-ahead intent precedes effecting operations.
9. Ambiguous external effects are not blindly retried.
10. There is no silent model, runtime, tool, disclosure, or authority fallback.
11. Reuse is checked before new execution.
12. Context is bounded, artifact-backed, checkpointed, and rotated.
13. RuntimeDriver and HarnessAdapter remain orthogonal.
14. Harness configuration is not treated as enforcement.
15. Parallel children do not share uncontrolled mutable state.
16. Infrastructure detail is diagnostic by default.

## Designed properties and implementation maturity

Current evidence is tracked in [STATUS.md](STATUS.md). This table summarizes the architectural direction rather than replacing that evidence record.

| Property | Architectural meaning | Current development maturity |
|---|---|---|
| Resumable | Work can continue through checkpoints and replacement Attempts | Partial |
| Forkable | Address, Work, or Attempt can branch from immutable state and reconcile through Commit | Design foundation only |
| Durable | Address, Canon, Work, events, artifacts, Outcomes, Candidates, and Commits survive workers | Demonstrated on one node and separately reproduced |
| Reusable | Active Work, accepted Outcomes, procedures, artifacts, checkpoints, and negative results prevent duplicate spend | Equivalent-work reuse separately reproduced |
| Token-managed | Situation compilation, lazy retrieval, artifacts, checkpoints, and Attempt rotation prevent context exhaustion | Partial |
| Tool-loop capable | Inner harnesses can repeatedly invoke models and typed tools | Real model-backed loop separately reproduced |
| Continuously executable | Work can run unattended under finite limits and continue through bounded Attempts | Bounded Attempt demonstrated |
| Parallelizable | Parent Work governs isolated Child Work loops and reconciles results | Reference Parent/Child behavior separately reproduced; real OpenCode loops pending |

## Explicit non-claims

The architecture does not, by itself, claim:

- universal containment of actively adversarial workloads;
- that Firecracker, KVM, containers, or any other runtime are unbreakable;
- production high availability or disaster recovery;
- semantic correctness of model output;
- independent verification without a separate verifier;
- cryptographic immutability without a configured evidence or witness layer;
- safe automatic merge of concurrent work;
- equal credential-isolation strength across every third-party harness;
- that a persistent workspace is authoritative.

## Component relationship

```text
Agent Anything
  human collaboration and organizational surface

Attexa Arc Harness
  open-source durable work identity, Situation, lifecycle, authority,
  Outcomes, Commit, accretion, and evidence linkage

Attexa Arc
  managed private intelligence environment and execution integration

Attexa Witness
  evidence and verification provider

ActionLease
  bounded external-action capability provider

Memory Box
  optional semantic retrieval and indexing provider
```

These are modular implementations around a stable kernel. None is the definition of the kernel itself.
