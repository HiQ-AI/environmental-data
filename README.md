# Environmental Data

Find environmental data across sources. Compare candidates, preserve provenance
and match the data to the question you are trying to answer.

Use it in research, product comparisons, procurement, reporting, assessment or
your own workflow. Install a source-specific plugin to stay within a requested
database, the published-EPD query plugin for declarations, or the aggregate
plugin when the question calls for multiple sources. This marketplace contains
no editor, modeling tool or audit expert.

## Install

Add the marketplace in Claude Code:

```text
/plugin marketplace add HiQ-AI/environmental-data
```

Choose the plugin you need, for example:

```text
/plugin install environmental-data-hiqlcd@environmental-data
```

```text
/plugin install environmental-data-epd@environmental-data
```

```text
/plugin install querying-lca-datasets-expert@environmental-data
```

Codex CLI 0.161.0 also accepts the native marketplace. Use its own plugin manager;
see [installation and migration](docs/INSTALLATION.md). Native plugin installation
loads skills and declared roles, not the business CLI or credentials. Prepare
the selected independent native CLI **0.7.0** separately using its pinned archive
and full SHA256. One private core produces distinct, compiled-scope executables;
this public repository contains only metadata and operating instructions.

## Plugins

<!-- catalog:start -->
| Plugin | Description |
| --- | --- |
| [HiQLCD](plugins/environmental-data-hiqlcd/README.md) | Search and match published HiQLCD environmental process datasets using the compiled hiqlcd source scope, preserving coordinates and access limitations. |
| [HiQLCD-AL](plugins/environmental-data-hiqlcd-al/README.md) | Search and match published HiQLCD-AL environmental process datasets using the compiled hiqlcd-al source scope, preserving coordinates and access limitations. |
| [CALCD](plugins/environmental-data-calcd/README.md) | Search and match published CALCD environmental process datasets using the compiled calcd source scope, preserving coordinates and access limitations. |
| [CESI Li-ion Battery Database](plugins/environmental-data-hiq-cesi/README.md) | Search and match published CESI Li-ion Battery Database environmental process datasets using the compiled hiq-cesi source scope, preserving coordinates and access limitations. |
| [Ecoinvent](plugins/environmental-data-ecoinvent/README.md) | Search and match published Ecoinvent environmental process datasets using the compiled ecoinvent source scope, preserving coordinates and access limitations. |
| [CarbonMinds](plugins/environmental-data-carbonminds/README.md) | Search and match published CarbonMinds environmental process datasets using the compiled carbonminds source scope, preserving coordinates and access limitations. |
| [Agri-footprint](plugins/environmental-data-agrifootprint/README.md) | Search and match published Agri-footprint environmental process datasets using the compiled agrifootprint source scope, preserving coordinates and access limitations. |
| [EF](plugins/environmental-data-ef/README.md) | Search and match published EF environmental process datasets using the compiled ef source scope, preserving coordinates and access limitations. |
| [AusLCI](plugins/environmental-data-auslci/README.md) | Search and match published AusLCI environmental process datasets using the compiled auslci source scope, preserving coordinates and access limitations. |
| [BAFU](plugins/environmental-data-bafu/README.md) | Search and match published BAFU environmental process datasets using the compiled bafu source scope, preserving coordinates and access limitations. |
| [BioEnergieDat](plugins/environmental-data-bioenergiedat/README.md) | Search and match published BioEnergieDat environmental process datasets using the compiled bioenergiedat source scope, preserving coordinates and access limitations. |
| [ELCD](plugins/environmental-data-elcd/README.md) | Search and match published ELCD environmental process datasets using the compiled elcd source scope, preserving coordinates and access limitations. |
| [NEEDS](plugins/environmental-data-needs/README.md) | Search and match published NEEDS environmental process datasets using the compiled needs source scope, preserving coordinates and access limitations. |
| [OzLCI](plugins/environmental-data-ozlci/README.md) | Search and match published OzLCI environmental process datasets using the compiled ozlci source scope, preserving coordinates and access limitations. |
| [Recycled Plastics](plugins/environmental-data-recycledplastics/README.md) | Search and match published Recycled Plastics environmental process datasets using the compiled recycledplastics source scope, preserving coordinates and access limitations. |
| [USDA Crop Data](plugins/environmental-data-usda/README.md) | Search and match published USDA Crop Data environmental process datasets using the compiled usda source scope, preserving coordinates and access limitations. |
| [USLCI](plugins/environmental-data-uslci/README.md) | Search and match published USLCI environmental process datasets using the compiled uslci source scope, preserving coordinates and access limitations. |
| [Worldsteel](plugins/environmental-data-worldsteel/README.md) | Search and match published Worldsteel environmental process datasets using the compiled worldsteel source scope, preserving coordinates and access limitations. |
| [Published EPD Data](plugins/environmental-data-epd/README.md) | Search published EPD declarations with traceable publishers, declared units, methods/modules, validity, access restrictions and cursor pagination. This is data retrieval, not EPD audit or certification. |
| [Environmental Data (Aggregate)](plugins/querying-lca-datasets-expert/README.md) | Query and match environmental data across published background sources and EPD declarations, preserving provenance, units, access limits and coverage gaps. |
<!-- catalog:end -->

The aggregate retains stable ID `querying-lca-datasets-expert`. Plugin package
versions are independent of the CLI and do not reset its account identity.

## Sources and coverage

The [live background-source directory](https://x.hiqlcd.com/api/relic/sources)
provides published versions and system models. The aggregate's [dated source
inventory](plugins/querying-lca-datasets-expert/SOURCES.md) records observed
coverage, not permanent account rights. Single-source plugins use separately compiled commands, not a `scoped` selector.
The aggregate has a compiled closed set; remote additions cannot expand it. Source conflicts, unsupported opaque-key tools and
cross-source responses fail rather than silently broadening the query.

Published EPD declarations use their existing separate query service and retain
publisher, declared unit, method/module, validity, restrictions and pagination.
A declaration is not automatically interchangeable with a background process.
Neither query plugin performs EPD audit or certification.

Directory visibility is not numerical access. Commercial values depend on
account entitlements; free-source labels do not waive owner terms or permit
redistribution. Numerical coverage varies by version, dataset, method and
indicator. Preserve missing or restricted values and unresolved needs.

## Your data and permissions

Send only authorized fields needed for the query, not an entire workbook when
selected inputs suffice. Keep credentials out of conversations and do not borrow
another application's tokens. Public metadata and EPD search need no local login;
background business queries and MCP tools retain the CLI's existing authentication.

Queries do not bind/import data, edit models, calculate a footprint, submit
business records, notify people or certify results. Preserve source coordinates,
units and applicability evidence. See [capabilities](docs/CAPABILITIES.md).

Workbook operations need a separately available, properly licensed spreadsheet
capability. Anthropic's [official XLSX skill](https://github.com/anthropics/skills/blob/main/skills/xlsx/SKILL.md)
and [its license](https://github.com/anthropics/skills/blob/main/skills/xlsx/LICENSE.txt)
are references, not bundled dependencies. See [spreadsheet requirements](docs/SPREADSHEETS.md).

## Compatibility and evidence

[Compatibility](docs/COMPATIBILITY.md) distinguishes native format/installation,
actual CLI queries and remaining acceptance gaps. [Distribution](docs/DISTRIBUTION.md)
records this delivery's scope, runtime contract and evidence. This publication
does not switch production Desktop's catalog or release Desktop.

A candidate, an accessible record and a suitable value are different things.
Keep provenance, coverage and access limits visible when applying a result.

## Contributing and support

See [catalog maintenance](CONTRIBUTING.md). Report reproducible problems in
[GitHub Issues](https://github.com/HiQ-AI/environmental-data/issues) with platform,
plugin/CLI version and a redacted error. Do not attach credentials or private inputs.
Repository-authored metadata, guides, roles and scripts are MIT licensed. CLI
software, databases and services retain their own terms; see [LICENSE](LICENSE)
and [third-party notices](THIRD_PARTY_NOTICES.md).
