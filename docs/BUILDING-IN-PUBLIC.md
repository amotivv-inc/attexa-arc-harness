# Building Arc with Arc

Attexa Arc Harness should be one of its own earliest serious users.

This is not a claim that the project can already build itself autonomously. It is a development discipline: as the kernel becomes capable, its own architecture, implementation, review, verification, releases, and accumulated knowledge should increasingly pass through the same durable Work model offered to other projects.

Public status changes follow [the status and milestone process](STATUS-UPDATES.md). The repository is updated when the project's evidence state changes, not merely because development activity occurred.

## Why dogfood the harness

Using Arc to build Arc helps answer questions that diagrams alone cannot:

- Can a new worker accurately understand the current project without replaying every conversation?
- Does Work survive a failed model, process, provider, or runtime?
- Can parallel builders and reviewers operate without uncontrolled shared state?
- Are authority, evidence, and official state transitions legible?
- Does completed Work make the next Work cheaper or more accurate?
- Can an outsider reproduce a result from public artifacts and contracts?
- Do the agent-facing abstractions remain ergonomic under real pressure?

A feature that is difficult to use while building Arc is a signal that the abstraction may be wrong.

## The public project as an Address

Conceptually, this repository can be represented as:

```text
Public Arc Harness Address
  |
  +-- Canon
  |     accepted architecture
  |     released contracts
  |     approved RFCs
  |     current compatibility commitments
  |
  +-- Work
  |     issues, commissions, child work, and verification
  |
  +-- Attempts
  |     human, agent, and deterministic execution episodes
  |
  +-- Outcomes
  |     patches, reviews, tests, benchmarks, and limitations
  |
  +-- Candidates
  |     proposed procedures, decisions, assertions, and failures
  |
  +-- Commits
  |     accepted merges, releases, and official transitions
  |
  +-- Evidence
        artifact digests, conformance results, and release manifests
```

Git remains the source-control system. GitHub remains the public collaboration surface. Arc supplies the durable Work, context, authority, truth, and evidence relationships around them.

## The repository as the first Arc Practice pilot

This repository is also the first intended test of [Arc Practice](practice/README.md).

A fresh person or agent with no access to the private development conversations should be able to enter the repository and determine:

- what the project exists to do;
- which architecture and processes are currently accepted;
- what has been implemented, separately reproduced, or only specified;
- what remains unavailable or unproven;
- which public claims may be advanced;
- when an RFC, milestone, provenance record, or status update is required;
- what the next valid piece of Work is.

The test should use the [Continuity Handoff Test](practice/CONTINUITY-HANDOFF-TEST.md). Missing or ambiguous instructions discovered by the participant are defects in the public workplace and should become explicit Work.

The project should not record this pilot as a passed milestone until a genuinely fresh participant has completed the test and the evidence has been accepted.

## What to publish

Public development may publish structured records such as:

- the bounded Commission or problem statement;
- the Outcome Contract and acceptance criteria;
- the architecture generation and relevant source digests;
- implementation and verifier Attempt metadata;
- produced patch or commit identifiers;
- test commands and observed results;
- resource use and provider-reported cost where useful;
- Decision Requests and the accepted answer;
- known limitations and unresolved questions;
- Candidate procedures, assertions, and negative results;
- release manifests and checksums.

The goal is to make the work independently understandable, not to maximize the volume of telemetry.

## What not to publish

Building in public does not mean publishing everything.

Do not publish:

- private chain-of-thought or hidden model reasoning;
- credentials, tokens, cookies, private keys, or auth profiles;
- customer, employee, partner, or personal data;
- undisclosed vulnerabilities or weaponized exploit detail before remediation;
- private infrastructure addresses or operational secrets;
- copyrighted or licensed material without permission;
- raw transcripts merely for spectacle;
- claims of verification unsupported by a stated verifier and method.

A concise structured Outcome with evidence is more valuable than a performative transcript dump.

## Evidence language

Kernel truth classes and public project-status vocabulary serve related but distinct purposes.

The kernel may represent:

```text
reported
platform_observed
self_tested
independently_verified
externally_reconciled
operator_accepted
canonical
```

Public project updates use:

```text
development-tested
separately reproduced
publicly reproducible
externally reviewed
```

Use **separately reproduced** when a distinct project-controlled verifier reruns the work. Reserve **independently verified** or **externally reviewed** for a verifier whose organizational and operational independence is stated.

Examples:

- “The builder says the feature is complete” is worker-reported.
- “The process exited zero and produced these bytes” is platform-observed.
- “The builder's own test suite passed” is self-tested or development-tested.
- “A separate Claude Sonnet verifier reran the suite through Attexa Arc” is separately reproduced.
- “An outside security firm evaluated a stated scope” may be externally reviewed.
- “A maintainer merged the result” is operator-accepted and, for the repository, canonical.

These statements should not be collapsed into a single “passed” label.

## A public Work cycle

A mature public development cycle may look like:

```text
Issue or RFC
    |
    v
Commission with explicit Outcome Contract
    |
    +-- Builder Attempt
    |     isolated branch or overlay
    |     bounded tools and inference
    |
    +-- Reviewer Attempt
    |     separate context and authority
    |
    +-- Deterministic checks
          formatting, tests, race checks, secret scan
    |
    v
Parent reconciliation Outcome
    |
    v
Pull request with artifacts and limitations
    |
    v
Human review and explicit merge
    |
    v
Accepted Candidates and new project Canon
```

The system should make this easier than manually reconstructing it, not add ceremonial bureaucracy to small changes.

## Release evidence

A future release should include, as appropriate:

```text
source archive
commit and architecture digest
versioned contracts
build and test results
software bill of materials
checksums
adapter conformance matrix
known limitations
security notes
agent and human review record
release Commit and signature
```

No release should claim more assurance than its evidence supports.

## Progressive dogfooding

### Stage 1: Documentation and issues

Use Arc concepts to structure architecture, RFCs, problems, acceptance criteria, and decisions while execution remains mostly manual. Run the first Continuity Handoff Test against the repository.

### Stage 2: Bounded implementation Work

Run selected implementation and verification Attempts through the reference kernel. Publish sanitized Outcomes and audit bundles.

### Stage 3: Parallel builders and reviewers

Use isolated Child Work, separate tool leases, and parent reconciliation for real pull requests.

### Stage 4: Recurring project operations

Use Standing Commissions for dependency review, issue triage, documentation drift, release preparation, and conformance monitoring.

### Stage 5: Portable public evidence

Allow independent users to verify release and adapter evidence without trusting an Attexa-operated service.

## Resource discipline

Using agents publicly does not justify unbounded spend. Arc should demonstrate:

- deterministic checks before model use;
- reuse and no-op detection;
- small Situation headers and lazy context retrieval;
- tool-result artifact indirection;
- bounded Attempts and checkpoints;
- escalation to stronger models only when the work requires it;
- human attention directed toward semantic uncertainty rather than routine repetition.

## Public truthfulness

Dogfooding fails if Arc-generated records become marketing theater.

The project should say:

- what was attempted;
- what actually ran;
- which model, harness, runtime, and tools were used when relevant;
- which limits and authority applied;
- which evidence was separately reproduced or externally reviewed;
- what failed or remained incomplete;
- what became accepted project state.

That standard is itself part of the product.
