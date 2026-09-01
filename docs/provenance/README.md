# Public Import Provenance

This directory defines how a non-public Arc Harness Kernel development snapshot becomes a public source commit.

A local Git hash from an ephemeral development environment is useful for internal continuity, but it is not sufficient public provenance. The import record should connect the exact source bytes, separate reproduction evidence, public commit, and any sanitizing changes.

## Required chain

```text
Non-public development snapshot
        |
        v
Sanitized source archive
        |
        +-- SHA-256 digest
        +-- dependency manifest
        +-- secret scan
        +-- test and race-test results
        +-- separate reproduction report
        |
        v
Public import pull request
        |
        v
Public Git commit and optional release tag
        |
        v
Documented differences
```

## Required manifest fields

A public import manifest should include:

- schema version;
- related milestone;
- non-public development snapshot identifier;
- development environment class;
- coordinator description using the public product name Attexa Arc;
- sanitized source archive digest;
- dependency and license review result;
- secret scan result;
- test and reproduction report digests;
- public import commit;
- release tag, if any;
- exact differences from the non-public snapshot;
- known omissions and limitations.

Use [0000-template.json](0000-template.json) as the starting point.

## Rules

- Never represent a local development hash as a public repository commit.
- Never omit sanitizing changes from the differences list.
- Never publish credentials, private endpoints, customer data, or hidden reasoning.
- Prefer artifact digests and reproducible commands over narrative assurance.
- A public import is `PUBLICLY_AVAILABLE` only when a fresh checkout can build and run using public instructions.
- Public evidence should distinguish development testing, separate reproduction, public reproducibility, and external review.
