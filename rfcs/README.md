# Arc Harness RFCs

RFCs are the public mechanism for proposing material changes to Attexa Arc Harness architecture, contracts, compatibility, security boundaries, and governance.

## When an RFC is required

Use an RFC for changes to:

- Address, Situation, Commission, Work, Attempt, Outcome, Commit, or Accretion semantics;
- Canon, workspace, artifact, Candidate, Ledger, or evidence boundaries;
- public schemas and wire contracts;
- RuntimeDriver, HarnessAdapter, HumanTaskAdapter, Tool, Inference, Policy, or Evidence interfaces;
- truth classes, authority, idempotency, recovery, or reconciliation;
- context compilation and token-management semantics;
- fork, merge, parent/child, or Standing Commission behavior;
- compatibility, versioning, governance, or project marks;
- a security guarantee or explicit non-claim.

Routine implementation work, documentation fixes, and changes that preserve an accepted contract generally do not require an RFC.

## Process

1. Open an RFC issue using the RFC issue form.
2. Discuss the problem, scope, and whether an RFC is necessary.
3. Copy [0000-template.md](0000-template.md) to a proposed file such as `rfcs/0007-context-rotation.md`.
4. Open a pull request containing the RFC.
5. Refine the proposal using public review, prototypes, conformance tests, and evidence.
6. Maintainers record one of these outcomes:
   - **Accepted**
   - **Accepted provisionally**
   - **Rejected**
   - **Withdrawn**
   - **Superseded**
7. An accepted RFC may be implemented in one or more later pull requests.
8. The architecture and compatibility documentation must be updated when implementation changes the current public behavior.

## Decision standard

An RFC should explain:

- the problem, not only the proposed mechanism;
- how the proposal fits the abstraction tower;
- which existing invariants it preserves or changes;
- authority, truth, evidence, privacy, and failure behavior;
- context and resource impact;
- alternatives and reasons for rejecting them;
- migration and compatibility;
- how the behavior can be conformance-tested;
- what remains uncertain.

A prototype can support an RFC but does not automatically make it accepted. A maintainer opinion can decide an RFC during incubation but should still address material objections.

## Numbering

The RFC number is assigned when the pull request is ready for substantive review. Use `0000` while drafting if a number has not been assigned.

Accepted RFCs remain in the repository as part of the project's decision history. Later RFCs supersede rather than silently rewrite their decisions.

## Security exception

Do not use a public RFC to disclose an unremediated vulnerability. Follow [SECURITY.md](../SECURITY.md). A public RFC or decision record may be added after coordinated remediation when safe.
