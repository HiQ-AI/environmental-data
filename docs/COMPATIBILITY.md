# Compatibility and verification

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
