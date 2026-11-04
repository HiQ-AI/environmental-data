# Environmental Data

Find environmental data across sources. Compare candidates, preserve provenance and match the data to the question you are trying to answer.

Use Environmental Data in research, product comparisons, procurement, reporting, assessment or your own data workflow. You choose the use case. The current connector retrieves environmental **process datasets** from published database sources; the data's format and coverage should not be confused with a restriction to one profession or workflow.

## What you can do

- Search across published sources or constrain a query to a particular source, version and system model.
- Find candidates for materials, energy, transport, treatment and other data requirements, individually or in supported batches.
- Inspect source coordinates, dataset identity, reference product/unit and available geographical, temporal and technology evidence.
- Retrieve numerical results where available and authorized, explaining the indicator/method and its basis.
- Keep unresolved needs and justified proxies visible instead of forcing every request into a match.

A search result, an accessible record and a suitable value are different things. Environmental Data keeps those distinctions explicit.

## Install

This repository is an independent marketplace containing the Environmental Data plugin. It does not install Editor, modeling tools or review experts.

In Claude Code, add the marketplace:

```text
/plugin marketplace add HiQ-AI/environmental-data
```

Install Environmental Data:

```text
/plugin install querying-lca-datasets-expert@environmental-data
```

The technical install ID remains `querying-lca-datasets-expert`; the displayed product name is **Environmental Data**. Installation loads the plugin's guides and agent roles. It does **not** install the business CLI, log in, download databases or grant access to data.

Prepare `querying-lca-datasets` CLI **0.5.1** separately, verify its release and use its own login or controlled credential mechanism. See [installation and migration](docs/INSTALLATION.md) for supported platforms, archive verification and moving from the former shared marketplace.

## Plugin

<!-- catalog:start -->
| Plugin | Description |
| --- | --- |
| [Environmental Data](plugins/querying-lca-datasets-expert/README.md) | Environmental Data: search and match environmental process data across published database sources, preserving source, version, system model, units and applicability evidence. Access depends on source and account entitlements. |
<!-- catalog:end -->

The plugin package is versioned independently of its CLI. A brand or documentation update does not rename the executable, reset credentials or change the underlying service contract.

## Sources and coverage

The backing service publishes a [live source directory](https://x.hiqlcd.com/api/relic/sources). Sources observed include Ecoinvent, HiQLCD, CALCD, CarbonMinds, EF, AusLCI, BAFU, ELCD, USLCI and Worldsteel. The [dated source inventory](plugins/querying-lca-datasets-expert/SOURCES.md) records the complete observed list, versions, system models and coverage flags.

Directory visibility is not account access. Commercial values require the corresponding entitlements. A service's “free” flag does not waive the database owner's terms or grant redistribution rights. Numerical coverage varies by source, version, dataset, method and indicator; some published sources do not advertise LCIA results.

The product name does not imply that every environmental database or data type is connected. Additional sources are supported only when actually published and exposed by the service. This release does not add an EPD-document query service or an EPD audit engine.

## Your data and permissions

Use the minimum authorized input needed for a request. Do not upload an entire workbook when selected fields suffice. Keep credentials out of conversations and reports, and do not copy tokens from another application.

Environmental Data retrieves and proposes matches. It does not bind data into a model, import datasets, calculate a model, modify business records or issue certification. Preserve the source, version, model, units and applicability evidence when using a result. See [capabilities and boundaries](docs/CAPABILITIES.md).

## Workbook tasks

A task involving Excel may need a spreadsheet capability actually available and properly licensed in your host. It is not required for ordinary queries.

Anthropic's [official XLSX skill](https://github.com/anthropics/skills/blob/main/skills/xlsx/SKILL.md) and [its license](https://github.com/anthropics/skills/blob/main/skills/xlsx/LICENSE.txt) are references, not bundled or automatically installed dependencies. See [spreadsheet requirements](docs/SPREADSHEETS.md).

## Host support

Claude Code's native marketplace and plugin manifests are validated. Actual isolated marketplace installation is checked without a model call or business login; that is not end-to-end acceptance of every data source. This repository is not an official-directory listing.

Codex marketplace adaptation has not been implemented or tested. The root Cortex catalog preserves pinned CLI supply metadata for compatible Hosts, but existing production Desktop has not switched to this repository and this publication is not a Desktop release. See [compatibility and verification](docs/COMPATIBILITY.md).

## Examples

> Find candidate data for these requirements, preserving source, version, reference unit and unresolved items. Do not silently change the requested database.

> Compare these returned candidates by geography, reference period and technology. Explain what the available evidence does and does not establish.

> Retrieve the authorized numerical result for this exact dataset reference and indicator, and retain its source and unit basis.

## Contributing and support

See [catalog maintenance](CONTRIBUTING.md). Report reproducible issues in [GitHub Issues](https://github.com/HiQ-AI/environmental-data/issues) with the OS/architecture, plugin/CLI versions and a redacted error. Do not attach credentials, private materials or customer inputs.

Repository-authored metadata, guides, roles and scripts are MIT licensed. CLI binaries, third-party software, databases and service entitlements retain their own terms. See [LICENSE](LICENSE) and [third-party notices](THIRD_PARTY_NOTICES.md).
