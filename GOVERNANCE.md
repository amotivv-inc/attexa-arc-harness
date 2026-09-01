# Governance

Attexa Arc Harness is an open-source project initiated and currently stewarded by **amotivv, inc.**

The project is in an early formation period. Governance is designed to make architectural decisions legible and public while preserving enough decisiveness to build a coherent first implementation.

## Principles

Project governance should:

- protect the architectural integrity of durable governed work;
- prefer public reasoning and reproducible evidence;
- distinguish stable contracts from experimental implementations;
- welcome independent implementations and adapters;
- avoid capture by one model, runtime, cloud, or commercial service;
- support responsible participation by human and AI-assisted contributors;
- remain honest about uncertainty, security, and implementation maturity.

## Roles

### Project steward

amotivv, inc. is the initial Project Steward. During incubation, the Project Steward:

- appoints and removes maintainers;
- resolves decisions when consensus cannot be reached;
- controls official releases and project marks;
- manages security response and coordinated disclosure;
- protects compatibility and architectural coherence;
- may delegate responsibilities to working groups or maintainers.

### Maintainers

Maintainers are contributors with sustained responsibility for one or more project areas. Maintainers may review and merge changes, triage issues, guide contributors, and participate in release decisions within their scope.

Maintainer status is based on demonstrated judgment, constructive participation, technical contribution, and commitment to the project's principles. It is not purchased and does not arise automatically from employment, sponsorship, or volume of contributions.

### Contributors

Anyone may propose issues, RFCs, documentation, tests, adapters, code, or independent verification, subject to the contribution process and Code of Conduct.

### Working groups

The Project Steward may form public working groups around areas such as:

- kernel semantics;
- contracts and conformance;
- runtime and harness adapters;
- security and threat modeling;
- human performer and domain-attestation mechanics;
- evidence and verified actions;
- developer and agent ergonomics.

A working group must publish its scope, decision authority, membership, and outputs.

## Decision classes

### Routine implementation decisions

Maintainers may decide changes that do not alter public contracts, architectural invariants, compatibility, security claims, or governance.

### Architecture and contract decisions

Changes to durable object semantics, public schemas, adapter interfaces, authority, evidence, recovery, compatibility, or governance require an RFC.

The RFC process is described in [rfcs/README.md](rfcs/README.md).

### Security decisions

Security-sensitive matters may be handled privately until coordinated disclosure is safe. The public record should be completed after remediation to the extent doing so does not create unreasonable risk.

### Emergency decisions

The Project Steward may act without the normal public process to address an active vulnerability, legal obligation, service abuse, compromised release, or similar urgent risk. The action and rationale should be documented afterward when safe.

## Consensus and final authority

The project seeks rough consensus supported by evidence, prototypes, conformance tests, and clearly stated tradeoffs.

Consensus does not require unanimity. During incubation, the Project Steward retains final authority when:

- the project cannot reach a timely decision;
- competing changes would fragment core semantics;
- a proposal creates unacceptable security, legal, compatibility, or operational risk;
- the decision concerns official marks or commercial service commitments outside the open project.

Significant decisions should identify objections and explain why the selected path was chosen.

## Public record

The durable public record should live in:

- issues for problems and bounded proposals;
- RFCs for architectural and contract changes;
- pull requests for implementation and review;
- architecture decision records where useful;
- release notes and evidence bundles for shipped behavior.

Private chat, model context, or an internal meeting is not the canonical project decision record.

## Releases and versioning

Before `1.0`, the project may make breaking changes while it discovers the correct abstractions. Breaking changes must still be documented and should include migration guidance where practical.

Stable contracts will use semantic versioning once their compatibility expectations are explicitly declared.

Official releases are created by maintainers authorized by the Project Steward. Release artifacts should be reproducible and accompanied by tests, checksums, known limitations, and evidence appropriate to the maturity level.

## Independence and commercial relationship

The open-source project contains the kernel semantics, reference implementations, contracts, adapters, and conformance tools.

Attexa Arc is the managed workplace and commercial product built around the project. Commercial services may fund development, supply implementations, and participate in governance, but conformance claims must remain testable independently.

The Apache License permits independent use and forks. The license does not grant rights to use project or company marks beyond reasonable attribution. See [TRADEMARKS.md](TRADEMARKS.md).

## Future governance

The project may adopt broader or more neutral governance after multiple independent organizations depend on and contribute materially to it. Foundation membership or formal multi-party governance should follow demonstrated ecosystem need rather than precede a working community.

Any governance transition will require a public RFC and explicit treatment of trademarks, release authority, security response, compatibility, and stewardship of project assets.
