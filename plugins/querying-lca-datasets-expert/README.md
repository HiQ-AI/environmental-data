# Environmental Data (Aggregate)

Search and match environmental process data across published database sources, with traceable provenance and explicit applicability limits.

Use it in research, comparisons, procurement, reporting, assessment or the data workflow you choose. The current connector exposes environmental process datasets for materials, energy, transport, treatment and other requirements. Its current data format and coverage do not restrict your purpose to LCA, and do not imply that every database or data type is connected.

## What it does

Search published sources, inspect source/version/system-model coordinates and reference units, verify identifiers and propose justified matches or unresolved needs while preserving input-row identity. Retain geography, time and technology evidence rather than treating a search hit as a suitable factor.

## Published sources and current scope

The backing service's public directory currently advertises sources including HiQLCD, Ecoinvent, CALCD, CarbonMinds, Agri-footprint, EF, AusLCI, BAFU, ELCD, USLCI and Worldsteel. See the [dated source inventory](SOURCES.md) for the full observed list, versions, system models and coverage limits, and follow its live directory link for current metadata.

Catalog visibility is not access to numerical data. Commercial-source values require the relevant account entitlements; a service “free” flag does not grant redistribution rights. LCIA coverage varies: the listed Agri-footprint and Recycled Plastics versions do not advertise LCIA results. A new product name does not connect additional databases; unlisted sources are not claimed as supported.

Published declarations are available through the separate public `epd-search`
command. Retain publisher, declared unit, method/module, validity and restricted
markers; do not substitute declarations for background processes without an
explicit comparability basis. This aggregate keeps unprefixed CLI capabilities;
use a source plugin when the question is fixed to one database. Removing a
single-source scope is not a fallback for missing data or denied access.

## Install the plugin

In Claude Code:

```text
/plugin marketplace add HiQ-AI/environmental-data
```

```text
/plugin install querying-lca-datasets-expert@environmental-data
```

This loads instructions and agent roles, not a CLI, credentials or business data. This repository marketplace is not an official-directory listing. Prepare the CLI separately using [installation and integrity checks](https://github.com/HiQ-AI/environmental-data/blob/main/docs/INSTALLATION.md).

## Native CLI and requirements

- Public product name: **Environmental Data**. The install ID remains `querying-lca-datasets-expert` so existing installations and upgrades keep their identity.
- Plugin version: **0.6.0** (aggregate access and source-plugin distribution).
- CLI executable: `querying-lca-datasets`. CLI version: **0.6.0**.
- Catalog platforms: `darwin-arm64, darwin-x64, linux-arm64, linux-x64, win32-x64`. Missing platforms are unsupported by this catalog.
- Exact archive URLs, SHA256 and executable/skill paths: [release catalog](https://github.com/HiQ-AI/environmental-data/blob/main/marketplace.json).

Use CLI device/QR login or its existing controlled API-key configuration. Service entitlements determine available databases and values; public plugin instructions grant no database rights.

Start with the matching CLI's version and help. Do not guess commands or assume installation means readiness. Native Claude Code plugin installation does not interpret Cortex CLI provisioning fields. Codex 0.161.0 accepts the native marketplace format; see the evidence scope below. Production Desktop has not switched to this source. See [host compatibility](https://github.com/HiQ-AI/environmental-data/blob/main/docs/COMPATIBILITY.md).

## Limits and side effects

Read-only lookup does not bind data into a model, calculate impacts, import datasets or certify an EPD. A general workbook is not a supported bulk upload merely because it contains an inventory.

Use only authorized input, preserve originals, keep credentials out of conversations and inspect actual receipts/readback. Do not blindly repeat an uncertain write. [Shared capability and permission boundaries](https://github.com/HiQ-AI/environmental-data/blob/main/docs/CAPABILITIES.md) apply.

## Example request

> Find candidate background processes for these authorized inventory rows, preserving units, provenance and unresolved matches.

## Workbook tasks

Workbook inspection or editing may need a separate spreadsheet capability actually available and properly licensed in the host. This plugin does not bundle or automatically install one. Anthropic's [official XLSX skill](https://github.com/anthropics/skills/blob/main/skills/xlsx/SKILL.md) and [its license](https://github.com/anthropics/skills/blob/main/skills/xlsx/LICENSE.txt) are references, not proof of installation or redistribution rights. If unavailable, explain the specific gap and request CSV/JSON only where adequate; do not imply it preserves all workbook features. See [spreadsheet dependencies](https://github.com/HiQ-AI/environmental-data/blob/main/docs/SPREADSHEETS.md).
