# Source plugin distribution

Tracking: [product Feature](https://github.com/HiQ-AI/environmental-data/issues/1).
Shared runtime: [CLI source scopes](https://github.com/HiQ-AI/hiq-cortex-cli/pull/10),
merged revision `63a81cc1ee7cffd7ab491e420d0eaebece5ad107`, version `0.6.0`.

## Delivery boundary

This delivery provides independently installable plugins for these background
sources: `hiqlcd`, `hiqlcd-al`, `calcd`, `hiq-cesi`, `ecoinvent`, `carbonminds`,
`agrifootprint`, `ef`, `auslci`, `bafu`, `bioenergiedat`, `elcd`, `needs`, `ozlci`,
`recycledplastics`, `usda`, `uslci`, `worldsteel`; one published-EPD query plugin;
and one aggregate plugin. The acceptance target is 20 plugins. This is a delivery
inventory, not a permanent limit on this product.

The aggregate retains installation ID `querying-lca-datasets-expert`. Source
plugins use `environmental-data-<source>` and the EPD query plugin uses
`environmental-data-epd`. Each owns a distinct skill and references the same
published CLI release. Neither binaries nor query implementations are forked
per database. This marketplace contains no editor, audit expert or other product.

## Runtime and access contract

- Background plugins invoke `querying-lca-datasets scoped <code> ...`. The CLI
  rejects conflicting sources, unsupported tools and cross-source responses.
  Supported commands are `sources`, `search-datasets`, `verify-datasets`,
  `search-flows`, `verify-flows`, and source-limited semantic `search`.
- Opaque-key lookup, statistics and hotspot tools lack a verifiable single-source
  input contract in the current CLI. Source plugins reject them instead of
  guessing key encodings or retrieving a different source and hiding it later.
  Explicitly selected aggregate access retains these capabilities.
- The aggregate uses the unprefixed CLI and the account's server-enforced access.
  It preserves source/version/model, permissions, failures and coverage gaps;
  installing it does not authorize hidden source substitution.
- `scoped epd epd-search` queries the existing public read-only
  `/api/relic/epd/search` API. EPD publishers such as `eco`, `epditaly` and
  `epdnorge` belong to this declaration domain, not the background-source list.
  The response retains declared units, publisher, method/module, validity,
  restricted markers, metadata and cursor pagination. It neither audits nor
  certifies declarations. A declaration is not an interchangeable background
  process dataset.
- Public source metadata and published-EPD search deliberately work without
  local login. Authenticated background queries and MCP tools retain the
  existing login/API-key requirement. An access failure is never retried using
  a different identity, broader source or different data domain.
- Server access rules remain authoritative. Public metadata, plugin licenses
  and free-source labels do not grant data redistribution or commercial rights.
  Check source terms and account entitlements for the intended use.
- Runtime scopes constrain an invocation, not an operating-system shell. The
  same executable supports explicit aggregate invocations; no shell sandbox or
  narrower OAuth token is claimed.

## Acceptance evidence

Completed shared-runtime evidence:
- Supported Node 24 local CLI regression suite and final source-scope tests pass.
- Five-platform archives built and integrity checked; native macOS arm64
  version/help/missing-credential behavior executed locally.
- Live development CLI with an empty identity store returns only HiQLCD metadata
  in `scoped hiqlcd sources`; current latest is `1.5.0`.
- Live `scoped epd epd-search --query concrete --limit 1` returns an actual
  published declaration, publisher `eco`, declared unit `m3`, method `A2`,
  headline `GWP-total` / `A1-A3`, and cursor pagination.
- Codex CLI `0.161.0` accepts the existing native marketplace and installs its
  aggregate plugin in isolated configuration. This baseline does not establish
  acceptance of the expanded catalog or agent-driven skill use.

Completed distribution evidence:
- The actual [release](https://github.com/HiQ-AI/hiq-cortex-cli/actions/runs/41773480030)
  succeeded. The catalog pins its five CDN checksums; a fresh macOS arm64
  download matches its full digest and the native executable reports `0.6.0`.
- The complete 20-entry catalog validates, including generated native index,
  README, component paths and identical shared CLI pins across all plugins.
- Claude Code `2.1.317` strictly validates all manifests; both it and Codex
  `0.161.0` install all 20 entries through their real native plugin managers in
  isolated configurations. Installed skill files are byte-equal to sources.
- Reading installed HiQLCD and EPD instructions in each host and manually
  executing their documented scoped commands with the CDN native executable
  returns actual public metadata and published EPD data. Aggregate metadata
  returns the 18 published background sources. Conflicting source arguments
  fail with exit 3 and no successful stdout. No model-chosen workflow is claimed.

Remaining acceptance gate:
- Execute an authenticated background dataset query through the CLI's own
  authorized identity. No such credential was present at the last check;
  metadata, fixtures and EPD public access do not substitute this gate.
  The product Feature remains open; implementation/publication and product
  acceptance are tracked separately.

No paid model runs, business writes, Desktop release or production catalog
switch are part of this delivery. GitHub records execution and acceptance;
this document owns the distribution contract and evidence boundary.
