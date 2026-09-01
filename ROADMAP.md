# Roadmap

Attexa Arc Harness is in pre-alpha public development. This roadmap separates what has been demonstrated experimentally from what is available in this public repository and what is required before a stable release.

The roadmap is directional rather than contractual. Architecture-changing work should proceed through the [RFC process](rfcs/README.md).

## Status language

- **Demonstrated**: exercised in an experimental reference implementation and independently rechecked at least once.
- **Public**: source, tests, documentation, and reproducible setup are present in this repository.
- **Stable**: versioned compatibility expectations and migration commitments exist.
- **Production-ready**: supported operational controls, recovery, monitoring, and security review exist.

A feature may be demonstrated without yet being public or production-ready.

## Phase 0: Public foundation

**Status: in progress**

- [x] Establish the public repository.
- [x] Adopt Apache License 2.0.
- [x] Publish the project definition and core architecture.
- [x] Publish governance, security, contribution, trademark, and conduct policies.
- [x] Establish an RFC process.
- [x] Define how Arc will be used to build Arc in public.
- [ ] Configure repository labels, branch protection, private vulnerability reporting, and release permissions.
- [ ] Publish the initial threat model.
- [ ] Publish a compatibility and conformance vocabulary.

## Phase 1: Reproducible single-node kernel

**Experimental implementation: demonstrated**  
**Public repository: planned**

Import and normalize the Go reference implementation behind a reproducible local setup.

Target scope:

- Address Registry and Canon generations;
- Situation projection;
- Commission idempotency and equivalent-work reuse;
- durable Work and Attempt records;
- cursor-based events;
- Decision Requests and operator answers;
- checkpoint records;
- Outcome truth classes;
- Candidate quarantine;
- content-addressed artifacts;
- compare-and-set Commit;
- stale-generation conflict;
- cancellation without Canon mutation;
- service-restart persistence;
- deterministic reference worker;
- model-backed reference worker using caller-supplied credentials through Arc-mediated inference;
- unit, integration, race, and end-to-end tests;
- one-command local demonstration.

Exit criteria:

- an external contributor can clone, build, test, and run the complete Address-to-Commit loop without private infrastructure;
- no amotivv secrets, private endpoints, customer data, or deployment residue are present;
- the public audit bundle can be reproduced from a fresh environment;
- architecture claims in the README map to executable tests.

## Phase 2: Canonical Tool Plane and first real harness adapter

**Experimental Tool Gateway foundation: demonstrated**  
**Public multi-harness reproduction: planned**

Target scope:

- versioned canonical Arc Tool Contract;
- per-Attempt capability issuance, hashing, expiry, revocation, and invocation limits;
- filtered tool discovery;
- input/output schema validation;
- scope, path, parameter, and budget constraints;
- write-ahead tool invocation evidence;
- idempotent retries and ambiguous-effect reconciliation;
- artifact-backed large results;
- durable asynchronous operation seams;
- MCP frontend;
- `HarnessAdapter` interface separate from `RuntimeDriver`;
- first real OpenCode adapter;
- isolated HOME, configuration, cache, workspace, output, inference, and tool capability per Attempt;
- OS-enforced local sandbox where supported;
- exact model pinning and no silent fallback;
- conformance suite for adapters.

Exit criteria:

- one downstream harness runs through Arc without receiving the upstream model or tool provider credentials;
- tool catalogs differ correctly across two Attempts;
- cross-Attempt capability use fails closed;
- a harness cannot reach an ungranted provider through the Arc plane;
- the adapter can be replaced without changing Work, Outcome, or Commit semantics.

## Phase 3: Parent and parallel Child Work

**Status: active experimental development**

Target scope:

- Parent and Child Work graph;
- explicit role, dependency, budget, and join policy;
- independent child Attempts, event streams, capability bundles, and artifacts;
- isolated writable overlays and read-only views;
- `all_terminal` and `first_success` joins;
- simultaneous Builder and Reviewer harness loops;
- parent comparison of agreements, disagreements, limitations, and verification status;
- explicit reconciliation Outcome;
- one normal Commit that promotes selected results;
- cancellation and partial-result semantics;
- complete concurrent-run evidence bundle.

Exit criteria:

- two real child harness processes overlap in wall-clock execution;
- neither child can mutate the other child's workspace or canonical state;
- parent reconciliation is based on immutable Outcomes and artifact digests;
- no automatic merge is represented as a verified or canonical result;
- resource accounting is attributable to parent, child, Attempt, model, and tool.

## Phase 4: Resumable long-horizon Work and context management

**Status: planned**

Target scope:

- automatic checkpoint-to-replacement-Attempt continuation;
- crash recovery and provider-failure recovery;
- model escalation without losing Work identity;
- adaptive token and byte budgeting;
- Context Manifest with selected, summarized, omitted, and on-demand material;
- semantic relevance and freshness scoring;
- cross-artifact deduplication;
- checkpoint-before-compaction policy;
- model-specific output reserve and safety margin;
- Attempt rotation before context exhaustion;
- typed recovery and reconciliation of possibly executed effects;
- explicit partial Outcome when safe continuation is impossible.

Exit criteria:

- a multi-hour Work item crosses at least two model contexts without replaying its full transcript;
- an interrupted worker is replaced from durable state and checkpoint;
- a possibly executed external effect is reconciled before retry;
- context selection is inspectable and reproducible from its manifest.

## Phase 5: Forking, recurring work, and broader performers

**Status: planned**

Target scope:

- first-class Address, Work, and Attempt fork lineage;
- branch comparison and explicit merge Commit;
- Standing Commissions for scheduled and event-driven work;
- overlap, circuit-breaker, suspension, and notification policy;
- no-op and reuse evaluation on each occurrence;
- HumanTaskAdapter and Human Performer lifecycle;
- typed domain-attestation Outcome;
- deterministic service performers;
- attention stream across many Addresses;
- machine-callable affordances for valid next actions.

Exit criteria:

- one Address can branch from an immutable generation and reconcile through a governed Commit;
- recurring work runs through bounded Attempts rather than an immortal worker;
- a human attestation is bound to an exact subject and context digest;
- judgment, authorization, execution, evidence, and Canon acceptance remain separate objects.

## Phase 6: Runtime and ecosystem portability

**Status: planned**

Target scope:

- Agent Fleet RuntimeDriver;
- container RuntimeDriver;
- second and third real HarnessAdapters, expected to include Codex and Claude Code when compatible;
- external tool and action providers;
- provider capability and trust declarations;
- Address import/export;
- adapter registry and compatibility matrix;
- conformance badge policy;
- stable schema and protocol versioning;
- cross-version migrations.

Exit criteria:

- the same Work contract runs through at least two RuntimeDrivers and two HarnessAdapters;
- an Address can move between conforming deployments without losing identity, Canon, artifacts, or provenance;
- adapters pass a public conformance suite rather than relying on vendor claims.

## Phase 7: Evidence and verified actions

**Status: planned**

Target scope:

- portable evidence graph;
- verifier registry;
- independent verification Attempts;
- ActionLease-compatible bounded external authority;
- external-effect receipts and reconciliation;
- Attexa Witness provider integration;
- signed domain-attestation objects;
- release evidence bundles;
- offline verification tools;
- evidence retention and redaction profiles.

Exit criteria:

- an independent verifier can validate the relationship among Commission, Attempt, tool invocation, Outcome, Commit, and resulting artifact without trusting the originating UI;
- the implementation does not call a result verified without a verifier identity, method, scope, result, limitations, and evidence reference.

## Phase 8: Production hardening

**Status: future**

Target scope:

- PostgreSQL and object-storage implementations;
- migration framework;
- encrypted secrets and key rotation;
- tested backup and restore;
- high-availability deployment options;
- disaster-recovery procedures;
- observability, alerting, and incident response;
- retention, erasure, and legal-hold controls;
- performance and failure-injection testing;
- external security review;
- release signing and software bill of materials;
- support and compatibility policy.

A production release will require explicit security and operations criteria. Passing functional tests alone is not sufficient.

## Deferred adjacent research

The following matters may affect runtime profiles but are not the defining problem of Arc:

- specialized adversarial-execution hosts;
- alternative hypervisors and minimal trusted computing bases;
- disposable physical hosts;
- cyber-range containment;
- independent hardware attestation for every runtime.

Arc should describe the actual properties of a selected runtime without claiming that the Harness Kernel makes the substrate unbreakable.
