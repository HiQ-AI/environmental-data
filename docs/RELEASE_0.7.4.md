# CLI 0.7.4 pins and migration

All twenty plugins pin independent CLI 0.7.4 programs from the immutable
[producer index](https://download.hiq.earth/cli/environmental-data/releases/v0.7.4/index.json).
The exact projection is [cli-release.json](../cli-release.json); per-program
archive URLs and full SHA256 values are in [marketplace.json](../marketplace.json)
and each skill's `references/installation.json`.

Index SHA256: `ffdd21e0aa02db739d60575583bb05d55bfc968cf84af92eb3837c9601455e0c`.
Producer source: `0813919ac245c5fa73aca7a6150739b3ce143538`.

## Command changes

Business commands are `search '<complete requirement>' --json` and
`lookup '<exact returned key>' --json`. Retired `search-datasets`, generic
`call`/`describe`, verification and aggregate tool commands are not available.
Use the installed program's actual help rather than historical examples.
Single-source programs remain compiled to their database; the aggregate supports
only its compiled set. EPD uses the same commands for declaration retrieval,
not audit or certification. Never substitute another program to bypass scope.

Read the bundled skill before querying. It covers discovering the executable,
checking actual version/info, downloading the exact pinned installer into an
empty directory, checking the full SHA256, reading the script, and performing
preparation within existing host permissions. Plugin installation does not
itself install a business binary or grant credentials. Do not alter security
settings, copy another application's credentials or pipe downloads into shells.
Do not uninstall old binaries or delete credentials as part of this update.

Keep geography and other user requirements in the full natural-language query.
Use source/version coordinates and model preferences only as documented by the
actual command. Default output is a preview; inspect coverage and omitted paths.
`--full` means the full current response, not the whole database. Preserve
restricted values, actual access decisions and unknown applicability evidence.

## Host support

Claude Code 2.1.317 supports plugin skills and declared agent roles. Codex CLI
0.161.0 loads the plugin skills but does not register bundled agent Markdown as
roles. This update preserves existing role IDs and does not introduce a custom
Codex role mechanism. Use its installed skill directly.

## Packaging evidence and limits

[Producer run](https://github.com/HiQ-AI/cortex/actions/runs/41813936584)
completed five-platform builds, native CDN executable/signature checks and seal:
twenty programs across macOS arm64/x64, Linux arm64/x64 and Windows x64, totaling
100 archives. macOS programs are Developer ID signed and notarized; Windows
programs are unsigned.

The workflow overall failed in the separate post-seal Windows installer check:
sealed declaration digest and checked-out declaration bytes differed. That check
stopped before actual installation; its root cause and Windows installation are
not established by this release. Native Windows executable checks passed, which
is not installer acceptance. Publishing these pins does not claim that check
passed. Do not weaken validation or Windows trust controls to install.

This update is distribution metadata and compatible operating instructions,
not final normal-account business or all-host acceptance. Earlier 0.7.0 and
0.6.0 verification records remain historical. No Desktop release or production
catalog switch is included.
