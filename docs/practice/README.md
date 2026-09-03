# Arc Practice

## Status

**Accepted project direction; initial open method under development.**

Arc Practice is not yet a certification program, a finished consulting methodology, or evidence that a particular practitioner has been assessed. The purpose of these documents is to define the emerging discipline clearly enough to test it against real bodies of work.

## Definition

> **Arc Practice is the discipline of establishing and stewarding a durable workplace around an important body of work, so changing combinations of people, AI, services, vendors, and tools can contribute without the organization's understanding and ability to continue depending on any one of them.**

The Arc Harness Kernel supplies durable objects, state transitions, context, authority, evidence, and performer orchestration. Arc Practice helps an organization decide what those structures should mean in its actual work.

Software alone cannot determine:

- which body of work must endure;
- where its meaningful boundaries lie;
- what the organization accepts as current truth;
- which uncertainty must remain visible;
- whose judgment or authority is required;
- what should be reusable, superseded, expired, or forgotten;
- whether a new participant can accurately continue the work.

Those are matters of practice and stewardship.

## Vocabulary

### Arc Practice

The open discipline and method described in this directory.

### Arc Practitioner

A person or group applying Arc Practice to a real body of work.

An Arc Practitioner helps make the work legible, governable, continuable, and increasingly self-explanatory. The practitioner is not automatically a domain expert, domain attestor, authorized principal, verifier, or platform operator.

### Arc Steward

A person or group responsible for maintaining an established Arc workplace over time. Stewardship includes keeping the Situation current, preserving material uncertainty, retiring stale state, maintaining authority boundaries, and ensuring that accumulated knowledge remains useful.

### Attexa Certified Arc Practitioner

A possible future assessed credential for individuals who have demonstrated Arc Practice through an end-to-end practicum.

**No Attexa Certified Arc Practitioner program is currently offered.** No person or organization should imply present certification, endorsement, or assessed competence.

## The Arc Practice loop

```text
Bound the body of work
        |
        v
Recover the current Situation
        |
        v
Establish truth and uncertainty
        |
        v
Define roles, authority, evidence, and acceptance
        |
        v
Conduct consequential Work
        |
        v
Accrete useful results
        |
        v
Test continuity through handoff
        |
        v
Transfer and maintain stewardship
```

## Practice invariant: Independent Value

> **Arc Practice must leave the body of work materially better whether or not the organization subsequently purchases, continues, or expands any amotivv product or service. Successful practice is measured by durable improvement to the work, not vendor conversion.**

An Arc engagement may legitimately lead to a managed Attexa Arc or Agent Anything deployment, another Arc Commission, or another commercial relationship. Those are commercial outcomes rather than the definition of practice success.

A non-converting engagement can still be successful when the organization leaves with a more legible, governable, continuable body of work and durable artifacts, evidence, authority boundaries, accepted state, or operating understanding that remain useful without a subsequent amotivv purchase.

This separation matters because Arc Practice is intended to serve the body of work rather than manufacture dependency on the practitioner or on a particular platform.

### 1. Bound the body of work

Identify the enduring thing whose continuity matters: a platform, product, operating capability, research program, regulated process, transition, client matter, or another coherent body of work.

The boundary should be broad enough to survive individual tasks but narrow enough to remain governable.

### 2. Recover the current Situation

Bring together available artifacts, systems, testimony, decisions, active work, and operational evidence. Preserve distinctions among:

```text
known
directly evidenced
attributed
inferred
disputed
stale
missing
unknown
```

The goal is not to manufacture certainty. It is to make the organization's current knowledge and uncertainty explicit.

### 3. Establish the operating structure

Define what is canonical, what remains working state, who may commission and perform Work, what requires verification or domain judgment, and what may become official only through Commit.

### 4. Conduct real Work

Apply the method to consequential Work using appropriate combinations of humans, agents, and deterministic services. The practice must improve the work rather than add ceremony around it.

### 5. Accrete what should remain

Preserve accepted decisions, evidenced assertions, reusable procedures, significant artifacts, failed approaches, open questions, limitations, and dependencies. Do not preserve every token merely because it exists.

### 6. Test transfer

Introduce a qualified participant who did not establish the environment and determine whether they can orient, distinguish truth from inference, locate evidence, understand authority, perform a bounded task, and leave a coherent Outcome.

See [Continuity Handoff Test](CONTINUITY-HANDOFF-TEST.md).

### 7. Transfer stewardship

The workplace should become less dependent on the original practitioner. An internal steward or practice group should be able to maintain it using explicit procedures and current evidence.

## Relationship to the kernel

```text
Arc Harness Kernel
  supplies durable work primitives and enforcement boundaries

Arc Practice
  applies those primitives to an actual body of work

Arc Practitioner
  establishes and improves the workplace

Arc Steward
  maintains the workplace over time

Performers
  humans, agents, and services that conduct Work

Domain Attestors and Verifiers
  provide qualified judgment or evidence when required
```

The kernel can support Arc Practice, but it cannot replace organizational judgment. Arc Practice can operate before every kernel feature is implemented, but it should increasingly use the kernel as the public implementation becomes available.

## Open method, future credential

Arc Practice is intended to remain openly documented and usable without certification.

A future formal credential should be based on demonstrated practice, not completion of a short course or familiarity with vocabulary. A candidate would need to take a real or sufficiently realistic body of work through the method end to end and pass a continuity handoff assessment.

A future credential must not imply unrelated domain expertise. Arc competence and domain competence remain separate qualifications.

## Initial pilots

The intended progression is:

1. Apply Arc Practice to the Attexa Arc Harness repository itself.
2. Apply it to one real software or vendor-transition body of work.
3. Apply it to one meaningfully different non-software body of work.
4. Compare failures, measures, and handoff outcomes.
5. Publish a draft competency model and practicum rubric.
6. Consider a formal certification program only after the method has survived those pilots.

The first pilot is tracked through a public repository issue.

## Documents

- [Arc Practitioner Charter](ARC-PRACTITIONER-CHARTER.md)
- [Continuity Handoff Test](CONTINUITY-HANDOFF-TEST.md)
- [Building Arc with Arc](../BUILDING-IN-PUBLIC.md)
- [Thesis series](../thesis/README.md)
- [Public status process](../STATUS-UPDATES.md)

Material changes to the role, practice invariants, certification boundary, or handoff criteria should proceed through the project's RFC process.
