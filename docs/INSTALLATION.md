# Installation and migration

## Install one of two plugins

Add the marketplace in Claude Code:

```text
/plugin marketplace add HiQ-AI/environmental-data
```

For environmental databases:

```text
/plugin install environmental-data@environmental-data
```

For published EPD declarations:

```text
/plugin install epd-data@environmental-data
```

These are host interface commands, not shell commands. Installation loads skills
and declared roles; it does not install a CLI, sign in or grant data rights.

Codex CLI 0.161.0 also accepts the native marketplace:

```bash
codex plugin marketplace add HiQ-AI/environmental-data
```

```bash
codex plugin add environmental-data@environmental-data
```

```bash
codex plugin add epd-data@environmental-data
```

```bash
codex plugin list --json
```

Claude Code supports the database product's three roles. Codex 0.161.0 loads
plugin skills but does not register bundled agent Markdown as roles.

## Prepare the CLI

CLI 0.8.0 provides `environmental-data` and `epd-data` on macOS arm64/x64, Linux
arm64/x64 and Windows x64. Read the chosen skill and bundled
`references/installation.json`. It pins the archive, installer and complete
SHA256 from [cli-release.json](../cli-release.json).

Download into a new empty directory and verify the full SHA256. Inspect the
verified installer before running it from outside the download directory; do not
pipe an uninspected download into a shell. Retain manifest, LICENSE, NOTICE and
bin together. Follow host permissions and normal OS trust controls; Windows
binaries are unsigned. The exact verification boundary is in
[compatibility](COMPATIBILITY.md).

Before executing an existing same-name program, establish its managed ownership,
binary hash and scope. Never execute an unknown program to identify it. Installers
refuse unrelated files, directories, external links and unverifiable entries.
Keep conflicting entries and select independent install/bin directories when
necessary, then use the verified absolute path. Installers retain versioned
payloads, do not edit PATH or credentials, and do not stop other processes.

After installation, verify the actual program:

```bash
environmental-data version
```

```bash
environmental-data info --json
```

```bash
epd-data info --json
```

Then read actual search/lookup help. Business commands are only `search` and
`lookup`; retired tool-dispatch and `scoped` commands are not supported.

## Select the data domain

Use `environmental-data-query` for background datasets. The program embeds the
18 supported databases; `--sources 'hiqlcd|ecoinvent'` selects within that set,
optionally with advertised `source:version` coordinates. CESI uses backend source
`hiq-cesi`. `--model` accepts `cut_off`, `consequential` or `apos`. Put geography,
technology, time and functional constraints in the complete natural-language
query. Background search has no limit, cursor or publisher flags.

Use `epd-query` and `epd-data` for published declarations. This domain has actual
publisher selection, limit 1..100 and returned-cursor continuation. It does not
accept background sources/models. `environmental-data --kind epd` is rejected;
`epd-data --kind datasets` is rejected. Read the skill's parameter reference
before choosing flags, and pass exact returned keys into lookup.

## Authentication and continuation

Both programs reuse the existing data-client product store and normal device
flow. Public metadata and published EPD search require no local login; other
operations retain service authorization. `doctor` shows local credential
presence only, not account rights. Missing/rejected credentials require normal
`login`; the command presents the actual authorization link and polls until
completion. Keep one login task, its result and the original query, then continue
that query after successful authorization. Do not copy tokens, borrow another
product's credentials or switch identity to evade denial.

Restricted values, missing records, authentication errors and service failures
are separate facts. `DATASET_PERMISSION_UNAVAILABLE`/HTTP 503 does not establish
that the account lacks entitlement; preserve the code/requestId for support
without exposing keys, payloads or credentials.

## Migrate existing installations

The eighteen single-database active plugins are retired. Refresh the marketplace,
install `environmental-data`, and explicitly disable or uninstall former
single-database subscriptions through the host manager when no longer needed.
Select the original database inside the unified program with `--sources`; an old
subscription does not rename itself. EPD stays a separate `epd-data` product.

The 0.8.0 installer supports a narrow same-name managed upgrade from
`environmental-data` 0.7.4 or 0.7.5: verified ownership, complete manifest/binary
hash, unchanged dataset source set and exact known former publishers are required.
It removes the aggregate's EPD domain, retains the old payload/manifest and
credentials, and points the managed entry to the new datasets-only version.
Unknown scope, program, source, publisher and unrelated ownership changes remain
conflicts. It is not a generic compatibility or alias mechanism.

Old immutable releases remain available; migration does not automatically delete
old binaries, settings, credentials or data. Updating a plugin alone does not
upgrade its CLI. Reload the host when required. This publication does not release
Desktop or switch its production catalog.
