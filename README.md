# Environmental Data

Find environmental data candidates, match requirements, compare applicability and
retrieve authorized details. Preserve provenance, evidence gaps and access limits.

## Choose a plugin

This marketplace contains two products:

- `environmental-data`: query the supported environmental databases through one
  program; select one or several databases with `--sources`.
- `epd-data`: query published Environmental Product Declarations and their details.

These products do not perform EPD audits or certification. The `cortex-epd`
auditing expert in HiQ-AI/plugins is a separate product.

Add the marketplace in Claude Code:

```text
/plugin marketplace add HiQ-AI/environmental-data
```

Install the database product:

```text
/plugin install environmental-data@environmental-data
```

Or install the published-declaration product:

```text
/plugin install epd-data@environmental-data
```

Codex CLI accepts this native marketplace through its plugin manager. Native
installation loads skills, not the CLI or credentials. Claude Code supports the
three database roles; Codex CLI 0.161.0 does not register bundled agent Markdown
as roles. See [installation and migration](docs/INSTALLATION.md).

## Plugins

<!-- catalog:start -->
<!-- catalog:end -->

`environmental-data-query` is the database skill; `epd-query` is the declaration
skill. The database product also provides `data-searcher`, `data-matcher` and
`data-reviewer` roles. Each plugin carries its own complete preparation,
authentication, parameter, professional-query, result and example references.

## Query workflow

Use `search` to find candidates and `lookup` with exact returned opaque keys to
retrieve authorized details. Keep geography, technology, reference time and other
requirements in the full query. Use source/version and system-model selectors
only where supported; do not decode or construct keys.

The database program is datasets-only. Select databases with `--sources`; it
cannot query EPD through `--kind epd`. The declaration program is EPD-only, with
its actual publisher, limit and cursor options. Neither program is a fallback
for denied rights in the other domain.

Default output previews the received response and reports omissions. `--full`
returns that response in full, not the whole database. Comparisons retain the
sample's limits; no database-wide statistics, median or hotspot API is provided.

Keep source, version, model, reference product/unit, geography, reference period,
method/boundary and exact returned links with the evidence. Missing, restricted
and unavailable are different outcomes. See [capabilities](docs/CAPABILITIES.md).

## Sources and access

The [source directory](https://x.hiqlcd.com/api/relic/sources) publishes database
versions and models. The [source inventory](plugins/environmental-data/SOURCES.md)
records dated coverage, not account rights. The compiled source/publisher sets
cannot be expanded by a remote directory change. CESI retains backend code
`hiq-cesi`; it is selected within the database program, not a separate plugin.

Directory visibility and successful search do not establish numerical access.
Account entitlements and source terms control values and redistribution. Both
programs share the existing data-client product authentication; installation
confers no credential or database license. A service-unavailable error does not
mean the account was denied access. Never borrow another product's token or put
credentials and private materials in an issue report.

Queries do not import records, edit models, calculate a footprint, purchase
access, submit business records or notify people. Workbook handling requires a
separate properly licensed [spreadsheet capability](docs/SPREADSHEETS.md).

## Distribution

CLI 0.8.2 supplies two native programs on macOS arm64/x64, Linux arm64/x64 and
Windows x64. The [sealed projection](cli-release.json) pins every archive and
installer. This repository contains public metadata and operating instructions,
not private CLI implementation, binaries, database content or credentials.

The eighteen single-database active entries are retired. Existing users select
the unified database plugin explicitly; the catalog does not delete their old
programs, subscriptions, credentials or data. Managed `environmental-data`
0.7.4/0.7.5 installations have a verified one-way migration to datasets-only.
Older immutable releases remain unchanged.

[Distribution](docs/DISTRIBUTION.md), [compatibility](docs/COMPATIBILITY.md) and
[consumer synchronization](docs/CONSUMER_SYNC.md) distinguish packaging,
installation, host behavior and real-account evidence. Publishing this market
does not release Desktop or switch its production catalog.

## Contributing and support

See [catalog maintenance](CONTRIBUTING.md). Report reproducible problems in
[GitHub Issues](https://github.com/HiQ-AI/environmental-data/issues) with platform,
plugin/CLI version and a redacted error. Repository-authored metadata, guides,
roles and scripts are MIT licensed. Software, databases and services retain their
own terms; see [LICENSE](LICENSE) and [third-party notices](THIRD_PARTY_NOTICES.md).
