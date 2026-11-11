# Environmental Data

Let agents query LCA background databases and published EPDs directly: find
datasets, read details and GWP100, and pull inventories (LCI) and impact results
(LCIA). Every result carries its source, version, system model, unit and a web
link for human review.

## Install

In Claude Code:

```text
/plugin marketplace add HiQ-AI/environmental-data
/plugin install environmental-data@environmental-data
```

For published EPDs, install `epd-data@environmental-data` instead. Then ask in
plain language, e.g. "find the GWP of low-voltage electricity on the East China
grid and list its inventory". The agent installs the pinned CLI and walks you
through a browser login. Codex CLI can use the same marketplace; see
[installation](docs/INSTALLATION.md).

## Plugins

<!-- catalog:start -->
| Plugin | Description |
| --- | --- |
| [Environmental Data](plugins/environmental-data/README.md) | Find and match Environmental Data data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
| [EPD声明查询](plugins/epd-data/README.md) | Find and match Published EPD Data data to user requirements, compare applicability and retrieve authorized details while preserving provenance and access limits. |
<!-- catalog:end -->

The database plugin ships the `environmental-data-query` skill and three roles:
`data-searcher`, `data-matcher` and `data-reviewer`. The EPD plugin ships
`epd-query`.

## Commands

| Command | What it returns |
| --- | --- |
| `search` | Candidate datasets; filter by `--sources source[:version]`, `--model`, `--location` |
| `lookup` | Dataset details: description, boundaries, GWP100, access decision, web link |
| `lci` | Cumulative inventory (elementary flows) of one dataset |
| `lcia` | Impact results; several datasets at once, one method, or process contributions |
| `methods` | LCIA methods and indicators of a source, for choosing `lcia --method` |
| `trace` | One layer of supply structure: up to three suppliers or consumers, each with its own key |

`epd-data` provides `search` and `lookup` for declarations. Eighteen background
databases are covered, including HiQLCD, CALCD, ecoinvent, Carbon Minds,
Agri-footprint, EF, USLCI, ELCD and worldsteel; see the
[source inventory](plugins/environmental-data/SOURCES.md) and the live
[source directory](https://x.hiqlcd.com/api/relic/sources).

Example (HiQLCD 1.5.0, low-voltage electricity, East China grid): search to LCIA
in about 3 seconds, GWP100 0.7314 kg CO2-eq/kWh, consistent across `lookup`,
`lcia` and process contributions.

## Access

- Every signed-in user gets values from free databases.
- Commercial values require an administrator to enable the account for
  Environmental Data CLI, then one more `login`. Values stay limited to the
  databases the account has licensed; restricted rows say `GRANT_REQUIRED`.
- Installing a plugin grants no credential or database license.

## Reading results

Each result keeps source, version, model, reference product and unit, geography
and a `webUrl` such as
`https://www.hiqlcd.com/dataset/HiQLCD/1.5.0/CUT_OFF/<id>/<name>?dataset_ref=<key>`.
Open it to check the same dataset on the website. Missing, restricted and
unavailable are different outcomes; do not rank values whose methods, models or
boundaries differ. Queries never import records, edit models or purchase access.
See [capabilities](docs/CAPABILITIES.md).

## Distribution

The [sealed projection](cli-release.json) pins every CLI archive and installer
for macOS arm64/x64, Linux arm64/x64 and Windows x64. This repository holds
public metadata and instructions only, not CLI source, binaries, database
content or credentials. See [distribution](docs/DISTRIBUTION.md),
[compatibility](docs/COMPATIBILITY.md) and
[consumer synchronization](docs/CONSUMER_SYNC.md).

## Contributing and support

See [catalog maintenance](CONTRIBUTING.md). Report problems in
[GitHub Issues](https://github.com/HiQ-AI/environmental-data/issues) with
platform, plugin/CLI version and a redacted error. Repository-authored content
is MIT licensed; software, databases and services keep their own terms. See
[LICENSE](LICENSE) and [third-party notices](THIRD_PARTY_NOTICES.md).
