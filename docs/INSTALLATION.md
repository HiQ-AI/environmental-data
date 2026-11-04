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

## Prepare the shared native CLI

CLI **0.6.0** supports macOS arm64/x64, Linux arm64/x64 and Windows x64. The
[root catalog](../marketplace.json) pins each archive's exact URL, full SHA256
and relative executable. All plugins reference the same release.

Download into a fresh directory and verify the entire archive before extraction
or execution. Preserve its complete layout and use your platform's executable.
Do not guess a generic installer or pipe an uninspected script into a shell.

Check version/help, then the selected scope:

```bash
querying-lca-datasets version
```

```bash
querying-lca-datasets scoped hiqlcd sources --json
```

```bash
querying-lca-datasets scoped epd epd-search --query concrete --limit 5 --json
```

Public source metadata and EPD search need no local login. Other background
queries and MCP tools use this CLI's own device/QR authorization or an existing
controlled `QUERYING_LCA_DATASETS_API_KEY`. Use the intended account and its
entitlements. Never paste secrets in chat, inspect credential files, copy another
app's tokens, redirect authenticated requests or change identities to evade denial.

Source plugins keep `scoped <code>` on business commands. The CLI rejects source
conflicts, contaminated output and tools without a verifiable source contract.
Removing the prefix to avoid a rejection defeats the selected product boundary.
Scopes are invocation controls, not an OS shell sandbox or an entitlement grant.

## Existing installations

The aggregate keeps `querying-lca-datasets-expert`, its guide and role IDs, and
the CLI's existing identity store. Upgrade the native CLI to 0.6.0 for the new
source-scoped commands; older CLI 0.5.1 does not implement them. A plugin refresh
does not itself upgrade a separately installed CLI or reset credentials.

For the former `querying-lca-datasets-expert@hiq-plugins` entry, explicitly add
the independent marketplace, install its aggregate or selected source plugin,
then disable/remove the old host-plugin entry through the host's own interface.
Avoid two copies of the same role/skill in a session. Do not remove the CLI,
credentials or user data as part of migration. Reload the host if it requires it.
This repository does not silently migrate user settings or uninstall old entries.

The root Cortex catalog preserves CLI supply metadata for compatible Hosts.
This publication does not switch production Desktop or release a new Desktop.
Workbook handling is a separate optional [capability](SPREADSHEETS.md).
