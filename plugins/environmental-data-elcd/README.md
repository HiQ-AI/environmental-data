# ELCD

Query and match environmental process data published under source `elcd`.
Use the data for the question and workflow you choose; preserve its limitations.

## Install

```text
/plugin install environmental-data-elcd@environmental-data
```

For Codex, use its native plugin manager as documented in
[installation](../../docs/INSTALLATION.md). Prepare the independent native CLI
`environmental-data-elcd` **0.7.0** separately. This plugin supplies its own skill;
it does not bundle a binary, log in or grant database rights.

## Source boundary

Every business invocation uses the independently compiled `environmental-data-elcd` command.
The runtime rejects conflicting source arguments, cross-source responses and
opaque-key/unknown tools without a verifiable source contract. Do not replace the executable to work around a failure. Cross-source analysis requires explicit aggregate
selection; it is not a fallback for denied access or a missing match.

Inspect current versions/models with `environmental-data-elcd sources --json`. Background
queries use the CLI's own authorized login or controlled API key. Source terms,
account entitlements and numerical coverage remain authoritative. Missing or
restricted values are not zero; a directory entry is not a suitability verdict.

See [distribution and verification](../../docs/DISTRIBUTION.md),
[capabilities](../../docs/CAPABILITIES.md) and [spreadsheet requirements](../../docs/SPREADSHEETS.md).
