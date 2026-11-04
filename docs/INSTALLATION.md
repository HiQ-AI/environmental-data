# Installation and migration

## Choose a plugin

Add the marketplace in Claude Code:

```text
/plugin marketplace add HiQ-AI/environmental-data
```

Install the selected source, for example:

```text
/plugin install environmental-data-hiqlcd@environmental-data
```

For published declarations use `environmental-data-epd@environmental-data`.
For explicitly selected multi-source access use the stable aggregate ID
`querying-lca-datasets-expert@environmental-data`. Other source IDs appear in the
[generated catalog](../README.md#plugins).

Claude Code's slash commands are interface commands, not shell commands. Plugins
load skills and declared roles; no installation hook installs a binary, signs
in, calls a model, grants data rights or downloads a licensed database.

## Codex native installation

The pinned native format is accepted by Codex CLI **0.161.0**. Use its own plugin
commands, not Claude Code slash commands:

```bash
codex plugin marketplace add HiQ-AI/environmental-data
```

```bash
codex plugin add environmental-data-hiqlcd@environmental-data
```

```bash
codex plugin list --json
```

Choose the EPD or aggregate ID the same way. Native marketplace support does not
mean the host automatically installs the business CLI or supplies credentials.
See [actual verification](COMPATIBILITY.md) for tested scope and limitations.

## Prepare the selected native CLI

Version **0.7.0** supplies independent commands for macOS arm64/x64, Linux
arm64/x64 and Windows x64. Select the program belonging to the plugin:
`environmental-data-<source>`, `environmental-data-epd`, or aggregate
`environmental-data`. Their implementation shares one private core; each binary
embeds its own supported-source/publisher declaration.

The [catalog](../marketplace.json) pins each complete archive URL/SHA256 and
executable. [Sealed release metadata](../cli-release.json) additionally pins
per-command installers and checksums. Its producer index is
https://download.hiq.earth/cli/environmental-data/releases/v0.7.0/index.json .
Download into a new empty directory, verify the complete SHA256 before extraction
or execution, and retain manifest, LICENSE, NOTICE and bin together. macOS has
Developer ID/Hardened Runtime/JIT, timestamp and accepted notarization. Windows
is unsigned: normal Windows trust/SmartScreen controls remain applicable. Never
weaken security settings to install it.

Optional per-command `install.sh` / `install.ps1` URLs and exact script SHA256
are in the sealed metadata. Download and inspect the selected script, verify its
SHA256 against that record, then execute it from outside the downloaded directory.
Do not pipe an uninspected download into a shell. Installers retain the complete
versioned release, do not edit PATH or credentials, and do not stop running
processes. `ENVIRONMENTAL_DATA_INSTALL_ROOT` and `ENVIRONMENTAL_DATA_BIN_DIR`
only select installation destinations; they cannot change query scope. The
Windows installer has not yet been actually executed in this delivery; native
Windows archive/executable validation is separate evidence.

```bash
environmental-data-hiqlcd version
```

```bash
environmental-data-hiqlcd info --json
```

```bash
environmental-data-hiqlcd sources --json
```

```bash
environmental-data-epd epd-search --query concrete --limit 5 --json
```

Public metadata and published EPD queries need no local login. Authenticated
background queries and MCP tools reuse this data-client product family's normal
login or controlled `QUERYING_LCA_DATASETS_API_KEY`; it is not a token borrowed
from another product. Use the intended account and its server entitlements.
Never inspect credential files, paste secrets in chat, redirect authenticated
requests or change identities to evade denial. A compiled source boundary does
not grant licenses or narrow the OAuth token.

No `scoped` selector is supported. Single-source commands reject conflicting
sources, contaminated results and unsupported opaque-key tools. The aggregate
only supports its embedded set and preflights opaque keys using canonical source
metadata before tool execution. Installing another program is not an authorized
fallback for denied access or missing data.

## Existing installations

Plugin IDs, skill IDs and aggregate role IDs remain stable. Upgrade plugin
instructions and install the new program matching the selected plugin. Old
`querying-lca-datasets` 0.6.0 with a `scoped` prefix is the previous delivery,
not an equivalent substitute for these independent compiled programs. The old
binary is not silently replaced or uninstalled. Existing data-client login
identity is intentionally shared; migration neither resets nor copies secrets.
Refreshing a plugin alone does not install or upgrade its business program.

For the former `querying-lca-datasets-expert@hiq-plugins` entry, explicitly add
the independent marketplace, install its aggregate or selected source plugin,
then disable/remove the old host-plugin entry through the host's own interface.
Avoid two copies of the same role/skill in a session. Do not remove the CLI,
credentials or user data as part of migration. Reload the host if it requires it.
This repository does not silently migrate user settings or uninstall old entries.

The root Cortex catalog preserves CLI supply metadata for compatible Hosts.
This publication does not switch production Desktop or release a new Desktop.
Workbook handling is a separate optional [capability](SPREADSHEETS.md).
