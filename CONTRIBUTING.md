# Contributing to Attexa Arc Harness

Thank you for helping build a durable work harness for temporary intelligence.

The project is in pre-alpha development. The architecture is intentionally explicit, but many APIs and file layouts are not yet stable. Contributions that improve correctness, legibility, interoperability, security, evidence, and reproducibility are especially valuable.

## Ways to contribute

You can contribute by:

- reviewing the architecture and identifying contradictions or missing invariants;
- implementing kernel state machines, storage, drivers, adapters, gateways, or tools;
- creating conformance and failure-injection tests;
- documenting real use cases and operational constraints;
- improving developer and agent ergonomics;
- writing RFCs;
- reporting bugs or security issues;
- independently reproducing demonstrations and evidence bundles.

## Before starting significant work

Open an issue or RFC before making a substantial change to:

- the Address, Situation, Commission, Work, Attempt, Outcome, Commit, or Accretion model;
- durability, authority, truth, evidence, or recovery semantics;
- public contracts and schemas;
- RuntimeDriver, HarnessAdapter, HumanTaskAdapter, Tool, or Inference interfaces;
- compatibility or security guarantees.

Small fixes, tests, and documentation improvements may go directly to a pull request.

## Contribution workflow

1. Fork the repository.
2. Create a focused branch from `main`.
3. Make the smallest coherent change that solves the stated problem.
4. Add or update tests and documentation.
5. Run all available validation locally.
6. Commit with a clear message and Developer Certificate of Origin sign-off.
7. Open a pull request using the repository template.
8. Address review and preserve the public decision record.

## Developer Certificate of Origin

Contributions use the Developer Certificate of Origin 1.1 process. Add a `Signed-off-by` line to each commit:

```text
Signed-off-by: Your Name <your-email@example.com>
```

Git can add this automatically:

```bash
git commit -s
```

By signing off, you certify that you have the right to submit the contribution under the project's Apache License 2.0 terms. See <https://developercertificate.org/>.

Do not submit code, documentation, model output, datasets, or other material that you do not have the right to contribute.

## AI and agent-assisted contributions

AI-assisted and agent-produced contributions are welcome. The accountable human or organization submitting the pull request remains responsible for the contribution.

A pull request should disclose material automation in practical terms, for example:

- which agent or tool materially produced or transformed the change;
- whether an independent review or verification Attempt was used;
- which tests, evidence, and artifact digests support the result;
- known limitations or areas that were not independently checked.

You do **not** need to publish private chain-of-thought, hidden reasoning, credentials, customer data, or raw transcripts. Prefer structured evidence such as the Commission, Outcome Contract, produced patch, tests, verifier findings, and release manifest.

Generated code must be reviewed for:

- correctness and failure behavior;
- license and provenance risk;
- hidden credential or endpoint leakage;
- unsupported claims;
- unnecessary dependency introduction;
- violations of Arc's authority and truth boundaries.

## Architecture fit

Every substantive contribution should answer:

1. Which durable Arc object or adapter owns this behavior?
2. Does the change preserve the separation between Work and Attempt?
3. Does it change Canon only through Commit?
4. Does it keep provider credentials outside workers where the adapter claims to do so?
5. Does it distinguish worker claims from platform observations and verification?
6. Does it record intent before an effect?
7. Does it avoid silent fallback?
8. Does it bound context, authority, resource use, and disclosure?
9. Does it improve future Work without turning unaccepted output into truth?
10. Can the behavior be conformance-tested independently?

If a change forces ordinary agents to reason directly about host IDs, ambient credentials, provider quirks, unbounded transcript replay, or uncontrolled shared state, it probably belongs below the kernel or needs redesign.

## Testing expectations

New behavior should include the strongest applicable tests:

- unit tests for state and validation logic;
- integration tests across storage and process boundaries;
- race tests for concurrent Go code;
- conformance tests for adapters and providers;
- negative tests for denied, stale, expired, cross-Attempt, and revoked capabilities;
- restart and recovery tests for durable behavior;
- evidence checks that compare summaries to raw events;
- end-to-end tests for any claimed lifecycle.

A model's completion statement is not a test result. Record what the platform observed.

## Documentation style

- Use clear, precise language.
- Distinguish current implementation from target architecture.
- Use `MUST`, `SHOULD`, and `MAY` only when the document is intentionally normative.
- Avoid claiming verification without identifying the verifier and method.
- Prefer diagrams and examples where they make boundaries more legible.
- Keep provider-specific behavior inside adapters rather than the kernel definition.

## Commit and pull request scope

Keep commits and pull requests reviewable. Separate mechanical refactors from semantic changes. Do not combine an architecture change, broad formatting pass, and unrelated bug fix in one pull request.

## Security

Do not open a public issue for a suspected vulnerability. Follow [SECURITY.md](SECURITY.md).

Never commit:

- API keys, tokens, cookies, private keys, or credentials;
- customer or personal data;
- internal hostnames or private deployment details;
- production audit bundles that were not explicitly sanitized;
- hidden model reasoning or confidential prompts.

## Code of Conduct

Participation is governed by [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).

## Questions

Open a focused discussion issue when the question is not security-sensitive. For architecture changes, start with the [RFC process](rfcs/README.md).
