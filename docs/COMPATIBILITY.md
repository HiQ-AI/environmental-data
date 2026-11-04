# Compatibility and verification

## Supported distribution

CLI 0.7.5 supplies 20 independent programs on macOS arm64/x64, Linux arm64/x64
and Windows x64. The [sealed release projection](../cli-release.json) identifies
the exact artifacts, hashes and source revision. macOS distribution uses
Developer ID, Hardened Runtime, timestamp and notarization. Windows binaries are
unsigned; OS trust and SmartScreen controls remain applicable.

The [release run](https://github.com/HiQ-AI/cortex/actions/runs/41822886153)
completed all five builds, native execution checks for all 100 CDN programs and
final sealing. Its Windows installer job failed during archive extraction with
`Extraction failed`; installation and the subsequent 15 entry-protection cases
did not pass. The native archive-runtime probes passed in both runner and isolated
environments, which does not explain the extraction failure. Windows installer
acceptance remains incomplete; do not treat this release as a fully verified
Windows installation path.

## Native plugin hosts

Claude Code supports the marketplace's skills and declared agent roles. Codex
CLI 0.161.0 accepts the native marketplace and plugin skills, but does not register
bundled agent Markdown as roles. Its plugin skill namespace is derived from the
plugin manifest. The catalog still gives every skill its own distinct ID.

Both native plugin managers installed all 20 new plugin IDs in isolated
configurations. All 40 installed skill files match the published source bytes;
Claude's strict marketplace and plugin-manifest validation passed. This is native
installation evidence, not a model-selected query evaluation.

Native plugin installation does not install the business CLI, create credentials
or grant database rights. A plugin manager listing is not evidence that a model
selected a skill or completed a query. See [installation](INSTALLATION.md) for
program preparation and migration.

## Local regression scope

The 0.7.5 producer changes passed targeted tests for consumer generation, native
program scope, POSIX installation and Windows release-declaration validation.
Consumer generation checks all 20 unique skill IDs, exact program references,
installation metadata and the aggregate's three roles. CESI retains backend
source `hiq-cesi`.

POSIX installation tests exercise managed upgrades, repeated installation,
corrupt archives, unrelated entries and linked payloads. Rejected entries and
external sentinel files remain unchanged; unknown same-name programs are not
executed. Release-declaration tests compare the immutable Git blob digest while
allowing equivalent LF/CRLF checkouts, and reject changed source or content.

These local tests do not substitute actual Windows installer execution. Native
platform results and any remaining release limitation must be read separately
from the release record.

## Business and professional boundaries

Naming changes do not modify `search` or `lookup` service contracts. Existing
public-metadata and EPD evidence does not prove every account's background-data
or restricted numerical access. A successful search does not establish data
suitability, an industry-wide statistic, an audit or certification.

This release does not claim a new paid-model reasoning evaluation, all-platform
business-query acceptance or production Desktop activation. Credentials are not
borrowed from other products. Remaining product acceptance belongs to the
[product Feature](https://github.com/HiQ-AI/environmental-data/issues/1), not to a
plugin pin update.

Version-specific older evidence is preserved in the repository history and
[0.7.4 release record](RELEASE_0.7.4.md); it is not current installation guidance.
