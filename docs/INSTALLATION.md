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

CLI 0.9.2 provides `environmental-data` and `epd-data` on macOS arm64/x64, Linux
arm64/x64 and Windows x64. Read the chosen skill and bundled
`references/installation.json`. It pins the archive, installer and complete
SHA256 from [cli-release.json](../cli-release.json).

For the chosen product, read its bundled `references/installation.json`:
[environmental-data](../plugins/environmental-data/skills/environmental-data-query/references/installation.json)
or [epd-data](../plugins/epd-data/skills/epd-query/references/installation.json).
Select the `releases` entry for your OS and architecture and the `sh` installer
for macOS/Linux or `ps1` for Windows. Download the selected installer into a new
empty directory. Compare its complete SHA256 against `installers.sh.sha256` or
`installers.ps1.sha256` using `shasum -a 256`, `sha256sum`, or PowerShell
`Get-FileHash -Algorithm SHA256`. Inspect the verified script, then run it from
outside the download directory using `sh <absolute-script-path>`. On Windows,
use `powershell.exe -NoProfile -File <absolute-script-path>` only when execution
policy permits scripts; the Restricted policy blocks it. Do not pipe a download
into a shell or change execution policy. The installer verifies the selected
archive. If Windows policy blocks the installer, use the manual installation below.
Retain manifest, LICENSE, NOTICE and bin together. Follow host permissions and
normal OS trust controls; Windows binaries are unsigned. The exact verification
boundary is in [compatibility](COMPATIBILITY.md).

Before executing an existing same-name program, establish its managed ownership,
binary hash and scope. Never execute an unknown program to identify it. Installers
refuse unrelated files, directories, external links and unverifiable entries.
Keep conflicting entries and select independent install/bin directories when
necessary, then use the verified absolute path. Installers retain versioned
payloads, do not edit PATH or credentials, and do not stop other processes.

### Manual Windows installation

On Windows x64, open PowerShell and set the first two paths below to the chosen
product's bundled `installation.json` and a new, independent installation directory.
The directory must not already exist; do not use an existing managed entry or
replace an unknown program. The commands download the pinned archive into a new
temporary directory, verify its full hash, and extract it with Windows native tar.
Run the lines in order and stop if any command fails.

```powershell
$metadataPath = 'C:\absolute\path\to\installation.json'
$installDir = 'C:\absolute\path\to\new-install-directory'
$metadata = Get-Content -LiteralPath $metadataPath -Raw | ConvertFrom-Json
$release = $metadata.releases.'win32-x64'
$downloadDir = Join-Path ([IO.Path]::GetTempPath()) ([Guid]::NewGuid().ToString())
New-Item -ItemType Directory -Path $downloadDir -ErrorAction Stop | Out-Null
$archive = Join-Path $downloadDir 'release.tar.gz'
Invoke-WebRequest -Uri $release.url -OutFile $archive -UseBasicParsing
if ((Get-FileHash -LiteralPath $archive -Algorithm SHA256).Hash -ne $release.sha256) { throw 'Archive SHA256 mismatch' }
New-Item -ItemType Directory -Path $installDir -ErrorAction Stop | Out-Null
& "$env:SystemRoot\System32\tar.exe" -xzf $archive -C $installDir
if ($LASTEXITCODE -ne 0) { throw 'Archive extraction failed' }
$exe = Join-Path $installDir "$($metadata.program)-$($metadata.version)\bin\$($metadata.program).exe"
& $exe version
& $exe info --json
& $exe search --help
& $exe lookup --help
```

Keep the extracted manifest, LICENSE, NOTICE and bin together. This independent
installation does not replace a managed entry, modify PATH or migrate credentials.
Use the resulting absolute `$exe` path for subsequent commands.

After installation, use the trusted absolute path to the selected executable for
`version` and `info --json`; compare program, version and scope with its
`installation.json`. Read `search --help` and `lookup --help` using that same
path. For `environmental-data`, also read `lci --help`, `lcia --help`,
`methods --help` and `trace --help`. Its business commands are `search`, `lookup`,
`lci`, `lcia`, `methods` and `trace`; `epd-data` provides `search` and `lookup`.
Retired tool-dispatch and `scoped` commands are not supported.

## Select the data domain

Use `environmental-data-query` for background datasets. The program embeds the
18 supported databases; `--sources 'hiqlcd|ecoinvent'` selects within that set,
optionally with advertised `source:version` coordinates. CESI uses backend source
`hiq-cesi`. `--model` accepts `cut_off`, `consequential`, `apos` or `en15804`.
Direct background search accepts
`--location` (comma-separated location codes), `--limit` (1..100, default 20),
`--cursor` (the returned page cursor) and `--collapse` (group by activity). It
does not accept publisher selection. `--assist` uses the matching workflow and
cannot be combined with `--location`, `--limit`, `--cursor` or `--collapse`;
describe those requirements in the query instead. Preserve technology, time and
functional constraints in the complete natural-language query.

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

The 0.9.2 installer supports a narrow same-name managed upgrade from
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
