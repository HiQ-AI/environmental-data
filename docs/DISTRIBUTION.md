# Independent program distribution

Tracking: [product Feature](https://github.com/HiQ-AI/environmental-data/issues/1).

## Current 0.7.0 delivery

One private core and authoritative channel declaration generate independently
compiled single-database, published-EPD and aggregate programs. The public
repository contains their sealed distribution metadata and distinct operating
skills, not the private CLI implementation, credentials or database content.
The current inventory is 18 database plugins plus EPD and aggregate; it is not
a permanent product ceiling. Plugin IDs remain stable.

[cli-release.json](../cli-release.json) is the read-only producer projection,
not a second editable source list. Catalog CLI declarations must exactly match
the corresponding sealed plugin entry. It records version 0.7.0, source commit
`837d4759e1b3da43bf5965b25c18ac7959eec89d`, five platforms, 100 archives and
per-program installer/checksum digests. Producer index:
https://download.hiq.earth/cli/environmental-data/releases/v0.7.0/index.json .
Its exact original bytes have SHA256
`f2a4546f3348d8200bf4ec7e9246d8045ef46232acc7dac06677db834d532ae7`.

Each single-database program binds its source at compilation. Arguments,
environment, adjacent config, binary renaming and old scoped selectors do not
select a wider supported set. EPD uses the existing declaration protocol and
compiled publisher set, distinct from background data and the auditing expert.
The aggregate has an explicit closed source/tool/publisher set; a remote catalog
addition cannot expand it. Opaque keys are checked against canonical source
metadata before aggregate tool execution; unverifiable keys fail. Single-source
opaque-key tools remain unavailable rather than guessing provenance.

Server authorization and source terms remain authoritative. All programs share
the existing data-client product identity, not new rights or narrower OAuth
tokens. Errors and restrictions remain visible; no fallback changes identity,
source or data domain. A binary boundary is not an OS shell sandbox.

The real tag-triggered release completed five-platform native validation of all
100 CDN executables: archive/manifest/binary hashes, actual version and embedded
info, Mac Developer ID/runtime/timestamp/notarization Accepted, Windows actual
NotSigned, Linux signing not-applicable. Final seal was written only after all
platforms passed. A separate readback matched all five platform indexes and 60
installer/checksum file digests to the sealed projection. These are packaging
and execution checks, not platform business-query or professional acceptance.

Local source tests compiled all 20 Mac development programs and passed 4 regression
tests covering all source boundaries, local real-SDK HTTP/MCP error handling,
and actual POSIX archive install/reinstall/corruption protection. Real public
metadata returned each of 18 sources only in its own program, the aggregate closed
set, and an actual EPD declaration. No paid model or business write occurred.

Windows installer and normal-account authenticated background queries remain
unverified; neither public EPD success nor synthetic tests replaces them. Fresh native installation of all 20 plugins in both pinned hosts passed;
installed skills match source bytes. Three production CDN POSIX program installs
and six actual public queries from installed instructions passed on Mac arm64.
This does not claim model-selected execution. Full evidence is recorded in
[compatibility](COMPATIBILITY.md). No production Desktop switch or release is
part of this delivery. The Feature remains open for unmet product acceptance.

## Historical 0.6.0 evidence

The following records the earlier shared-runtime delivery. It does not establish
that new independent 0.7.0 instructions or programs were installed in a host.

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
