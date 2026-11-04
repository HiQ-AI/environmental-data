# Compatibility and verification

> Current pins and compatible commands: [CLI 0.7.4 migration and verification limits](RELEASE_0.7.4.md). The older version-specific instructions/evidence below are historical; do not use retired commands with 0.7.4. Windows installer verification has not passed.

## Current independent 0.7.0 programs

The sealed producer projection supplies 20 independent commands across macOS
arm64/x64, Linux arm64/x64 and Windows x64. All100 actual CDN programs executed
version/info and platform signature checks on their native target architecture.
This does not establish business-query acceptance on those platforms. Mac uses
formal Developer ID/notarization; Windows binaries are unsigned/NotSigned.

Fresh isolated installation of all 20 version-0.7.0 plugins passed through both
Claude Code 2.1.317 and Codex CLI 0.161.0 native plugin managers. Every installed
skill matches current source bytes; Claude Code strict marketplace and all
plugin-manifest validations passed. No login, model run or global configuration
change was required. The older evidence below remains historical. Native installation does not install a business
CLI, grant credentials or prove data suitability. Production Desktop is unchanged.

The Windows installer and normal-account authenticated background query remain
unverified. Public metadata/EPD, local fixtures and native version checks do not
replace either gate. [Current distribution contract](DISTRIBUTION.md).

## Current installed instructions and real calls

On macOS arm64, the exact checksum-verified production CDN POSIX installers
installed `environmental-data-hiqlcd`, `environmental-data-epd` and aggregate
`environmental-data` into an isolated destination. Actual version 0.7.0, embedded
info and native codesign verification passed. Complete releases/licenses remain
in their versioned installation directories; no login or PATH change occurred.

After reading each host's installed HiQLCD, EPD and aggregate skill, manually
executed its documented command with the matching production program:
- HiQLCD sources returned only HiQLCD metadata.
- EPD concrete search returned an actual declaration with a supported publisher
  and page cursor.
- Aggregate sources returned its compiled 18-source closed set, missing empty.
- Conflicting HiQLCD/Ecoinvent source arguments exited 3 with no success stdout.

All six host/instruction query executions passed. This is installed-instruction
and actual-program verification, not evidence of a model choosing a skill or
performing a reasoning workflow. No paid models or business writes occurred.

## Historical 0.6.0 host evidence

## Hosts

- **Claude Code 2.1.317:** the marketplace and all plugin manifests pass native
  strict validation. All 20 plugins install through the actual plugin manager
  using an isolated HOME/configuration. Installed skill files match their source
  bytes; this is more than listing available entries.
- **Codex CLI 0.161.0:** its native `plugin marketplace add` and `plugin add`
  commands accept the same marketplace. All 20 plugins install in an isolated
  CODEX_HOME, and installed skill files match their source bytes. No separate
  adapter, global permission change, login or model run was needed.
- **Cortex Hosts:** root `marketplace.json` preserves typed CLI supply metadata.
  This publication does not switch production Desktop's catalog or release
  Desktop. No new production Host acceptance is implied.

## Shared runtime

All entries pin CLI **0.6.0**, independently versioned from the plugin packages,
for macOS arm64/x64, Linux arm64/x64 and Windows x64. The shared CLI is published
from [reviewed source](https://github.com/HiQ-AI/hiq-cortex-cli/pull/10) through
[its actual native release workflow](https://github.com/HiQ-AI/hiq-cortex-cli/actions/runs/41773480030).
The downloaded macOS arm64 archive's full SHA256 matches the published checksum;
its verified native executable reports 0.6.0. No binaries are checked into this
marketplace and no per-database CLI implementation is forked.

The CLI's local regression tests cover source-parameter rejection before HTTP,
opaque-key/unknown-tool denial, cross-source and missing-provenance rejection,
public EPD query fields, retained restrictions and cursor pagination. Five native
archives passed integrity/layout/architecture checks; native macOS arm64
version/help/missing-credential behavior executed locally. This is not native
Windows/Linux business-query acceptance.

## Installed instructions and real calls

After native installation in each host, verification reads the installed HiQLCD
and EPD skills, confirms their scoped entrypoints and executes the documented
commands with the actual CDN native CLI:

- `scoped hiqlcd sources --json`: actual published source versions/models,
  containing only HiQLCD in scoped output.
- `scoped epd epd-search --query concrete --limit 1 --json`: an actual published
  declaration with publisher, declared unit, headline method/module and cursor.
- Aggregate `sources --json`: the live background directory currently has 18
  entries. This is public metadata, not per-source numerical lookup acceptance.
- Conflicting HiQLCD scope / Ecoinvent source: exit 3 before business HTTP, with
  no successful-result stdout.

These are manually executed commands from installed instructions, not evidence
that a model selected a skill or completed an end-to-end reasoning workflow. No
paid model run, original customer upload, business write or notification occurred.

## Remaining acceptance gap

The CLI's own normal identity currently has no credential. Authenticated
background dataset search and restricted numerical lookup have therefore **not**
been accepted against a real account. No token was borrowed from another app;
public EPD success, metadata and synthetic tests do not replace this gate. The
[product Feature](https://github.com/HiQ-AI/environmental-data/issues/1) stays open
until its remaining acceptance conditions are satisfied.

Native installation does not provision the business CLI, sign in, grant licenses
or prove data suitability. A successful query is not professional certification.
Preserve source terms, coverage, applicability and access limits. See the
[distribution contract](DISTRIBUTION.md).
