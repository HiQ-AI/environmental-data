# Installation and migration

## Claude Code plugin

```text
/plugin marketplace add HiQ-AI/environmental-data
```

```text
/plugin install querying-lca-datasets-expert@environmental-data
```

The marketplace name is `environmental-data`; the plugin's stable technical ID is `querying-lca-datasets-expert` and its display name is Environmental Data. These are Claude Code interface commands, not shell commands. The independent marketplace contains only this product.

Plugin installation loads instructions and agent roles, not a business CLI or credentials. No install hooks, automatic login, model calls or database downloads are bundled.

## Prepare the native CLI

The supported platforms for CLI **0.5.1** are macOS arm64/x64, Linux arm64/x64 and Windows x64. The [root catalog](../marketplace.json) pins each archive URL, full SHA256 and relative executable path. Choose your actual platform; do not run another platform's binary.

Download into a new directory, verify the entire archive digest before extraction/execution, and preserve the complete archive layout. Invoke the listed executable by its actual path or use the publisher's documented registration process with authorization. Do not guess a generic installer URL or pipe an uninspected remote script into a shell.

Start with `querying-lca-datasets version` and `querying-lca-datasets --help`. Discover command schemas through `list --json` / `describe <command>` where documented. Runtime command discovery is not permission to run a search or install another component automatically.

The CLI owns device/QR login. An existing controlled `QUERYING_LCA_DATASETS_API_KEY` takes precedence over its stored login. Use the intended account and entitlements. Do not paste secrets into chat, inspect credential files, copy Desktop/provider tokens, change endpoints or switch identities to bypass access rules. Installation does not grant commercial-source data rights.

## Moving from the shared marketplace

If you previously installed `querying-lca-datasets-expert@hiq-plugins`, the product now has its own marketplace and source of truth. It is no longer listed alongside other products in the current shared marketplace.

The install ID, CLI command, pinned CLI0.5.1 release and authentication contract have not changed. The marketplace namespace **has** changed, so this is an explicit host-plugin migration, not an automatic account or CLI upgrade.

1. Check your host's installed-plugin list. Disable the old `querying-lca-datasets-expert@hiq-plugins` instructions before enabling the independent copy, so two sets of roles/skills do not operate in the same session.
2. Add and install the independent marketplace using the commands above. Confirm the displayed product and installed source.
3. Once the independent plugin is available, remove the old host-plugin entry using the host's own uninstall interface. Do not delete the separately installed CLI, its credentials or user data as part of this migration.
4. Restart/reload the host session if it requires that for plugin discovery. Use the independent plugin's instructions and existing CLI thereafter.

A marketplace refresh is not an automatic migration. This repository does not silently uninstall old entries, move user configuration or broaden permissions. Older shared-marketplace revisions remain in Git history for traceability, not as a separately maintained product source.

## Other hosts

The root Cortex catalog carries existing CLI supply metadata for compatible Hosts, but production Desktop is not switched here by this publication. Codex marketplace installation has not been adapted or tested. Do not apply Claude Code marketplace commands to another host or modify host security settings to force compatibility.

For workbook handling see [spreadsheet requirements](SPREADSHEETS.md); for access, scope and side effects see [capabilities](CAPABILITIES.md).
