# Environmental Data

Query environmental data from a selected database, published EPD declarations or
multiple supported sources. Find candidates, compare applicability, match
requirements and retrieve authorized details while preserving provenance,
coverage gaps and access restrictions.

## Choose a plugin

The catalog contains 18 database plugins, one EPD plugin and one cross-source
plugin. Plugin ID and CLI name are identical. Database skills use `<source>-query`;
EPD uses `epd-query`, and the aggregate uses `environmental-data-query`.
Skill titles use Data Querying.

Add the marketplace in Claude Code:

```text
/plugin marketplace add HiQ-AI/environmental-data
```

Install the plugin for your data source:

```text
/plugin install hiqlcd@environmental-data
```

```text
/plugin install epd-data@environmental-data
```

```text
/plugin install environmental-data@environmental-data
```

Codex CLI 0.161.0 accepts the same native marketplace through its plugin manager.
Native installation loads skills, not the CLI or credentials. Claude Code
supports the aggregate's three roles; Codex 0.161.0 does not register bundled
agent Markdown as roles.

Read [installation and migration](docs/INSTALLATION.md) to prepare the selected
0.7.5 CLI and replace an old plugin subscription. The new IDs do not
automatically rename subscriptions or delete old programs and credentials.

## Plugins

<!-- catalog:start -->
| Plugin | Description |
| --- | --- |
| [HiQLCD 数据查询](plugins/hiqlcd/README.md) | Find and match HiQLCD data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [HiQLCD-AL 数据查询](plugins/hiqlcd-al/README.md) | Find and match HiQLCD-AL data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [CALCD 数据查询](plugins/calcd/README.md) | Find and match CALCD data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [中国锂电池碳足迹数据查询（CESI）](plugins/cesi/README.md) | Find and match China Li-ion Battery Carbon Footprint Database (CESI) data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [ecoinvent 数据查询](plugins/ecoinvent/README.md) | Find and match Ecoinvent data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [CarbonMinds 数据查询](plugins/carbonminds/README.md) | Find and match CarbonMinds data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [Agri-footprint 数据查询](plugins/agrifootprint/README.md) | Find and match Agri-footprint data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [EF 数据查询](plugins/ef/README.md) | Find and match EF data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [AusLCI 数据查询](plugins/auslci/README.md) | Find and match AusLCI data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [BAFU 数据查询](plugins/bafu/README.md) | Find and match BAFU data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [BioEnergieDat 数据查询](plugins/bioenergiedat/README.md) | Find and match BioEnergieDat data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [ELCD 数据查询](plugins/elcd/README.md) | Find and match ELCD data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [NEEDS 数据查询](plugins/needs/README.md) | Find and match NEEDS data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [OzLCI 数据查询](plugins/ozlci/README.md) | Find and match OzLCI data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [Recycled Plastics 数据查询](plugins/recycledplastics/README.md) | Find and match Recycled Plastics data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [USDA Crop Data 数据查询](plugins/usda/README.md) | Find and match USDA Crop Data data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [USLCI 数据查询](plugins/uslci/README.md) | Find and match USLCI data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [Worldsteel 数据查询](plugins/worldsteel/README.md) | Find and match Worldsteel data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [EPD声明查询](plugins/epd-data/README.md) | Find and match Published EPD Data data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [环境数据跨库查询](plugins/environmental-data/README.md) | Find and match Environmental Data (Aggregate) data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
<!-- catalog:end -->

The aggregate provides `data-searcher`, `data-matcher` and `data-reviewer` roles.
Source-specific plugins have no additional agent roles.

## Query workflow

Use `search` to find candidates and `lookup` to retrieve authorized details.
Describe geography, technology, time and other requirements in the full query;
use source/version and system-model selectors only where supported. Preserve
opaque keys exactly for lookup. The selected skill documents the actual inputs.

Default results provide a candidate preview with coverage information. `--full`
returns the complete current response, not the whole database. Comparisons over
returned candidates must retain their sample limits; these plugins do not expose
a database-wide statistics or hotspot API.

Keep source, version, model, product, unit, geography, reference period and
available method/indicator evidence with each result. A candidate, an accessible
record and a suitable value are different things. Missing and restricted values
must remain visible. See [capabilities](docs/CAPABILITIES.md).

## Sources and access

The [source directory](https://x.hiqlcd.com/api/relic/sources) publishes background
source versions and system models. The aggregate's
[source inventory](plugins/environmental-data/SOURCES.md) records dated coverage,
not permanent account rights. Each program embeds its supported sources or
publishers; a remote directory addition cannot expand that boundary.

Published EPD declarations retain publisher, declared unit, method/module,
validity and restrictions. A declaration is not automatically interchangeable
with a background process. Neither plugin performs an EPD audit or certification.

Directory visibility is not numerical access. Account entitlements and source
terms control commercial values and redistribution. Compiled scope does not
grant licenses. Public metadata and EPD search need no local login; background
queries retain the data client's normal authentication.

Send only authorized fields needed for a query. Do not put credentials in a
conversation or borrow another application's tokens. Queries do not import data,
edit models, calculate a footprint, submit business records or notify people.
Workbook handling requires a separate properly licensed
[spreadsheet capability](docs/SPREADSHEETS.md).

## Distribution and evidence

One private core produces 20 independently scoped native programs across five
platforms. This repository contains public metadata and operating instructions,
not the CLI implementation, database content, binaries or credentials.
[Distribution](docs/DISTRIBUTION.md) defines the artifact and authorization
contract. [Compatibility](docs/COMPATIBILITY.md) distinguishes packaging,
installer, host and business-query evidence.

Publication does not release Desktop or switch its production catalog.

## Contributing and support

See [catalog maintenance](CONTRIBUTING.md). Report reproducible problems in
[GitHub Issues](https://github.com/HiQ-AI/environmental-data/issues) with platform,
plugin/CLI version and a redacted error. Do not attach credentials or private
inputs. Repository-authored metadata, guides, roles and scripts are MIT licensed.
CLI software, databases and services retain their own terms; see [LICENSE](LICENSE)
and [third-party notices](THIRD_PARTY_NOTICES.md).
