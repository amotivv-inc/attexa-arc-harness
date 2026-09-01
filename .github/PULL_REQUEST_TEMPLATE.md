## Summary

Describe the change and the result it is intended to produce.

## Problem or Commission

What concrete problem does this solve? Link the issue or RFC where applicable.

## Architecture ownership

Which layer owns this behavior?

- [ ] Surface or agent-facing API
- [ ] Arc Harness Kernel
- [ ] Tool, inference, policy, or evidence plane
- [ ] RuntimeDriver
- [ ] HarnessAdapter or HumanTaskAdapter
- [ ] Provider or deployment substrate
- [ ] Documentation or governance only

## Change type

- [ ] Bug fix
- [ ] Feature preserving an existing contract
- [ ] Architecture or contract change with RFC
- [ ] Refactor
- [ ] Tests or conformance
- [ ] Documentation
- [ ] Security hardening

## Evidence

List the validation performed and distinguish its strength.

```text
Commands run:
Observed results:
Independent verification:
Artifacts or digests:
Known limitations:
```

## Authority, failure, and compatibility

Describe any effect on:

- capabilities or credentials;
- Canon and Commit semantics;
- idempotency and ambiguous-effect reconciliation;
- cancellation, restart, or recovery;
- context size or resource use;
- public schemas, APIs, storage, or adapter compatibility.

Write `None` where a category is not affected.

## AI or agent assistance

Describe material AI or agent involvement, if any. Identify the practical workflow, tests, and review used. Do not include private chain-of-thought, credentials, customer data, or confidential prompts.

## Checklist

- [ ] The change is focused and reviewable.
- [ ] Current behavior and target architecture are not conflated.
- [ ] New behavior has appropriate tests.
- [ ] Denied, stale, expired, cancelled, or failure paths are covered where relevant.
- [ ] Worker claims are not represented as platform-observed or independently verified facts.
- [ ] Canon changes occur only through Commit.
- [ ] No silent model, runtime, tool, disclosure, or authority fallback was introduced.
- [ ] Documentation and changelog entries are updated where needed.
- [ ] No secrets, private endpoints, customer data, or unsafe audit material are included.
- [ ] Commits include `Signed-off-by` lines.
