# Security Policy

Attexa Arc Harness coordinates durable state, agent context, capabilities, credentials, tool execution, and official state transitions. Security reports are taken seriously.

## Project maturity

The project is currently **pre-alpha**. The public repository and initial reference implementation are not yet production-ready or covered by a long-term security-support policy.

Until versioned releases are published, security work targets the current `main` branch and the newest public technical preview. Older experimental snapshots may not receive fixes.

## Reporting a vulnerability

Do not report suspected vulnerabilities through a public GitHub issue, pull request, discussion, or social post.

Email:

```text
security@amotivv.com
```

Use the subject:

```text
ARC HARNESS SECURITY VULNERABILITY
```

Include, where available:

- affected commit, version, component, adapter, or deployment mode;
- vulnerability type and expected security boundary;
- prerequisites and configuration;
- minimal reproduction steps;
- proof-of-concept code or evidence;
- observed and potential impact;
- whether credentials, customer data, or third-party systems were accessed;
- suggested remediation or containment;
- your preferred attribution.

Please encrypt sensitive material or request a secure transfer method before sending credentials, private customer data, or a weaponized exploit.

## Response targets

We aim to:

- acknowledge a report within 48 hours;
- provide an initial assessment or request for more information within 72 hours;
- coordinate remediation and disclosure according to severity, exploitability, affected users, and release maturity.

These are response targets, not service-level guarantees.

## High-priority security areas

Reports are especially useful when they demonstrate:

- provider credentials reaching an untrusted worker contrary to the adapter's declared mode;
- cross-Address, cross-Work, cross-Attempt, or cross-tenant data access;
- reuse of an expired, revoked, foreign, or stale capability;
- unauthorized Tool Gateway discovery or invocation;
- path traversal, symlink escape, writable-overlay escape, or runtime isolation failure;
- model or tool fallback that bypasses declared policy;
- canonical state mutation outside Commit;
- stale-generation overwrite or compare-and-set failure;
- replay or duplicate execution of a consequential effect;
- audit, Ledger, evidence, or artifact tampering that is represented as valid;
- mismatch between raw events and reported usage or verification summaries;
- hidden secret, customer data, or private endpoint leakage in exports;
- privilege escalation in `arcd`, the CLI, bridges, drivers, adapters, or reference deployment;
- denial of service that crosses a stated resource or isolation boundary;
- unsafe deserialization, command injection, or arbitrary code execution in a trusted component.

## Model and prompt behavior

Unexpected, incorrect, or policy-inconsistent model output is not automatically a software vulnerability.

It becomes a security issue when the behavior crosses an enforced boundary, for example when untrusted content:

- gains authority it was not granted;
- obtains a secret or unauthorized data;
- invokes a tool outside its capability bundle;
- changes Canon outside Commit;
- causes an external effect that should have required approval or reconciliation;
- falsifies evidence accepted by a trusted component.

Prompt injection reports should therefore identify the boundary that failed, not only the text that influenced a model.

## Good-faith research

When testing the project:

- use systems and data you own or have explicit permission to test;
- minimize access to sensitive information;
- stop after establishing the vulnerability and impact;
- do not persist, alter, publish, or exfiltrate unnecessary data;
- avoid denial of service against shared or production systems;
- allow reasonable time for remediation before public disclosure;
- do not use a public Attexa service as a target unless permission is explicitly granted.

We will make a good-faith effort to work constructively with researchers who follow these principles.

## Security claims and evidence

The project distinguishes:

```text
worker-reported
platform-observed
self-tested
independently verified
externally reconciled
operator-accepted
canonical
```

A test passing is not equivalent to a security audit. A source review is not equivalent to a live adversarial probe. A sandbox is not represented as unbreakable. Documentation and release notes should state the actual evidence supporting a claim.

## Coordinated disclosure

After remediation, we may publish:

- affected versions and configurations;
- impact and severity;
- mitigations and fixed versions;
- credit according to the reporter's preference;
- technical detail appropriate to protecting remaining users.

Security advisories and release notes will be used when public releases exist.
