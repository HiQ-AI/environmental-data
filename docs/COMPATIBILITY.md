# Compatibility and verification

## Supported distribution

CLI 0.8.1 has two programs, `environmental-data` and `epd-data`, targeting macOS
arm64/x64, Linux arm64/x64 and Windows x64. The
[sealed projection](../cli-release.json) identifies the exact revision, scope,
archives and hashes. macOS uses Developer ID, Hardened Runtime, timestamps and
notarization. Windows binaries are unsigned; normal OS trust and SmartScreen
controls remain applicable.

The [0.8.1 release run](https://github.com/HiQ-AI/cortex/actions/runs/41954305504)
is the authority for actual build, CDN native execution, sealing and Windows
installer results. Those results are pending in this preparation branch.
Version 0.8.0 passed five builds, five native jobs and sealing but failed Windows
PowerShell 5.1 parsing of localized migration JSON. Its sealed bytes are retained.
Version 0.8.1 emits an ASCII-only PowerShell script containing all business-scope
identity fields (protocol, source codes and publishers), without localized labels.
This source correction alone is not actual Windows installation acceptance.

## Native plugin hosts

Claude Code supports skills and the database product's three declared roles.
Codex CLI 0.161.0 accepts native marketplace plugins and skills but does not
register bundled agent Markdown as roles. Each plugin's skill has its distinct
ID: `environmental-data-query` or `epd-query`.

The two-product change retains the two program/plugin IDs from the former market
and removes the eighteen single-database entries. Earlier twenty-plugin host
installation evidence does not establish installation of these regenerated
packages. Current catalog, manifest and installed-content evidence must be
identified separately; no new model-selected query evaluation is claimed.

Native installation does not install a business CLI, create credentials or grant
data rights. A host listing does not prove a model chose a skill or completed a
query. Follow [installation](INSTALLATION.md) for program preparation.

## Local producer regression

The 0.8.0 implementation passed targeted native-development and HTTP checks for
the two domains, all eighteen selectable database sources, model forwarding,
unknown source refusal, EPD isolation, authorized lookup routing, preserved
restriction fields and preview/full output. These HTTP fixtures do not establish
real-account authorization.

Consumer generation checks the two distinct skills, local reference reachability,
installation projection, common references and three database roles. Synchronizer
checks cover old-channel/ID rejection, explicit root registration, sealed CLI pin
binding, no-op, rollback/tampering and PR recovery.

POSIX installer execution covers managed upgrades, repeat installation, corrupt
archives, unrelated entries and links. The explicit 0.7.4/0.7.5 aggregate-to-0.8.1
datasets migration passes for both old versions and rejects unknown source,
publisher and protocol changes while retaining the old manifest. The old source
and publisher sets were compared with their actual tagged declarations.

Windows migration and entry-protection cases are present in the native release
verifier; source review and POSIX execution do not prove those cases passed on
Windows. Read the actual release job outcome separately.

## Real-account query evidence

The 0.8.0 development CLI reused the normal product authentication and returned a
real HiQLCD candidate. Formal lookup then returned HTTP 503 with
`DATASET_PERMISSION_UNAVAILABLE`. This is service unavailability, not evidence of
denied entitlement or a restricted numerical row. Current numerical retrieval
acceptance remains blocked; no successful value is claimed from that request.

Earlier HiQLCD authorization success does not establish ecoinvent rights, another
account's access or every source/model/version combination. Public metadata and
EPD search likewise do not prove numerical entitlement. Preserve the service's
actual accessDecision, errors and evidence; do not relogin or switch identity to
work around an unavailable permission check.

This release does not claim all-platform business queries, a new paid-model
reasoning evaluation, EPD audit/certification or Desktop activation. Remaining
acceptance belongs to the
[product Feature](https://github.com/HiQ-AI/environmental-data/issues/1).
Version-specific older evidence remains in Git history and the
[0.7.4 record](RELEASE_0.7.4.md), not current installation guidance.
