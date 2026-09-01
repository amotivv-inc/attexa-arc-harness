---
rfc: "0000"
title: "Replace with proposal title"
author: "Name or GitHub handle"
status: "Draft"
created: "YYYY-MM-DD"
updated: "YYYY-MM-DD"
requires: []
supersedes: []
superseded-by: []
---

# RFC 0000: Proposal title

## Summary

State the proposed change and its intended result in a few paragraphs.

## Problem

Describe the concrete problem, affected users or agents, current failure mode, and why the problem belongs in Arc rather than solely in a surface, provider, RuntimeDriver, or HarnessAdapter.

## Goals

- Goal one.
- Goal two.

## Non-goals

- Explicitly excluded concern one.
- Explicitly excluded concern two.

## Current behavior

Describe the current public architecture and implementation. Distinguish stable contracts, experimental behavior, and unimplemented design.

## Proposed design

Describe the proposed objects, state transitions, contracts, and interfaces.

Include diagrams and representative schemas where they improve legibility.

## Abstraction ownership

Explain which layer owns the behavior:

```text
Surface
Agent-facing API
Arc Harness Kernel
Capability plane
RuntimeDriver
HarnessAdapter or HumanTaskAdapter
Provider or substrate
```

## Invariants

List the existing invariants this proposal preserves.

Identify any invariant it changes and justify that change explicitly.

## Authority and security

Describe:

- identity and delegation;
- capability issuance, expiry, revocation, and scope;
- credential custody;
- approval requirements;
- fail-closed behavior;
- instruction versus data boundaries;
- likely abuse and attack paths.

## Truth, evidence, and auditability

Explain which statements are:

```text
worker-reported
platform-observed
self-tested
independently verified
externally reconciled
operator-accepted
canonical
```

Describe write-ahead intent, event ordering, evidence references, and how claims can be checked independently.

## Failure, cancellation, and recovery

Cover partial execution, process failure, provider failure, cancellation, ambiguous effects, restart, checkpointing, and safe retry.

## Context and resource impact

Describe token, byte, latency, compute, cost, disclosure, and human-attention effects. Explain reuse and no-op behavior.

## Compatibility and migration

Identify schema, API, storage, adapter, or behavior changes. Provide a migration strategy and rollback behavior.

## Alternatives considered

Describe meaningful alternatives, including keeping the current behavior, and explain why they were not selected.

## Conformance and acceptance tests

List tests an independent implementation must pass.

## Rollout

Describe staging, feature flags, experimental labels, metrics, and conditions for declaring the change stable.

## Open questions

- Open question one.
- Open question two.

## Decision

Maintainers complete this section when the RFC reaches a terminal decision.

- Status:
- Decision date:
- Decision makers:
- Material objections:
- Rationale:
- Required follow-up:
