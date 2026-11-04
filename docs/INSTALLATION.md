# Installation and migration

## Choose a plugin

Add the marketplace in Claude Code:

```text
/plugin marketplace add HiQ-AI/environmental-data
```

Install the selected source:

```text
/plugin install hiqlcd@environmental-data
```

Use `epd-data@environmental-data` for published declarations or
`environmental-data@environmental-data` for cross-source queries. The
[catalog](../README.md#plugins) lists all 18 database plugins.

These are host interface commands, not shell commands. Native installation loads
skills and declared roles; it does not install the business CLI, sign in, call a
model, grant data rights or download a licensed database.

## Codex native installation

Codex CLI 0.161.0 accepts the same native marketplace:

```bash
codex plugin marketplace add HiQ-AI/environmental-data
```

```bash
codex plugin add hiqlcd@environmental-data
```

```bash
codex plugin list --json
```

Codex 0.161.0 loads plugin skills but does not register bundled agent Markdown as
roles. Claude Code supports the aggregate's three declared roles.

## Prepare the selected CLI

Version 0.7.5 provides 20 independent commands on macOS arm64/x64, Linux arm64/x64
and Windows x64. Plugin ID and program name are identical: `hiqlcd`, `cesi`,
`epd-data`, `environmental-data`, and the other source names in the catalog.

Read the selected plugin's skill and its bundled `references/installation.json`.
It pins the exact archive, installer and complete SHA256 for each platform from
[the sealed producer projection](../cli-release.json). Download into a new empty
directory, verify the full SHA256 before extraction or execution, and keep
manifest, LICENSE, NOTICE and bin together. Inspect the checksum-verified
installer before running it from outside the download directory; do not pipe an
uninspected download into a shell.

Before using an existing same-name command, establish its ownership from the
managed versioned manifest, binary hash and compiled scope. Do not execute an
unknown same-name program to identify it. Installers refuse unrelated files,
directories, external links and unverifiable entries without replacing them.
If a name conflicts, retain the existing entry and choose an independent install
and bin directory; invoke the verified program by its absolute path.

Installers retain complete versioned releases, do not edit PATH or credentials,
and do not stop running processes. Installation destination settings cannot
change query scope. macOS uses Developer ID, Hardened Runtime, timestamp and
notarization; Windows binaries are unsigned. Keep normal OS trust controls enabled.

```bash
hiqlcd version
```

```bash
hiqlcd info --json
```

```bash
epd-data search 'concrete' --limit 5 --json
```

The business commands are `search` and `lookup`. Use the full natural-language
query for geography and other requirements; preserve opaque keys for lookup.
Read the selected skill for supported `sources` and `system_model` options,
preview coverage and `--full` semantics. Do not use retired tool-dispatch or
`scoped` commands.

Public metadata and published EPD search need no local login. Background queries
use the data client's existing normal authentication and server entitlements.
Migration does not rename its OAuth identity or credential location. Never copy
credentials, borrow another product's tokens or change identity to evade denial.
A compiled source boundary does not grant a database license.

## Migrate existing installations

0.7.5 changes plugin, skill and role IDs as well as program names. Refresh the
marketplace, install the desired new plugin ID through the host's native manager,
and disable or uninstall the former plugin entry through that same manager.
Subscriptions to old IDs do not automatically become subscriptions to new IDs.

- Database plugin/program: `environmental-data-<source>` becomes `<source>`;
  the former CESI entry becomes `cesi` (its backend source remains `hiq-cesi`).
- EPD plugin/program: `environmental-data-epd` becomes `epd-data`.
- Aggregate plugin: `querying-lca-datasets-expert` becomes `environmental-data`;
  its program remains `environmental-data`.
- Skills use `<source>-query`, `epd-query` and `environmental-data-query`.
- Aggregate roles are `data-searcher`, `data-matcher` and `data-reviewer`.

There are no aliases or parallel legacy entries in the current catalog. Old
immutable releases remain available as historical records. Migration does not
automatically delete old programs, user settings, credentials or data. Updating
a plugin alone does not upgrade its CLI. Reload the host when required.

This publication does not switch production Desktop's catalog or release
Desktop. Workbook handling remains an optional [capability](SPREADSHEETS.md).
See [compatibility and evidence](COMPATIBILITY.md) for the tested boundaries.
