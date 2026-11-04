# Distribution contract

## Products and artifacts

Environmental Data supplies 18 source-specific database programs, one published
EPD program and one cross-source program. One private implementation and one
channel declaration produce all 20 programs. This repository publishes the
consumer catalog, native plugin manifests, skills, roles and sealed installation
metadata. It contains no private CLI implementation, credentials or database
content.

Release 0.7.5 targets macOS arm64/x64, Linux arm64/x64 and Windows x64: 100 native
archives in total. The immutable producer index is:

https://download.hiq.earth/cli/environmental-data/releases/v0.7.5/index.json

The checked-in [cli-release.json](../cli-release.json) is the producer's sealed
projection. It records the source revision, declaration digest, platform
archives, installer digests and consumer names. It is not a second editable
source list. Catalog CLI entries must match that projection exactly.

## Naming

Plugin ID and CLI name are identical. Database entries use their source names,
such as `hiqlcd`, `ecoinvent` and `cesi`. Published declarations use `epd-data`;
the aggregate uses `environmental-data`.

Database skills use `<source>-query`. The EPD skill is `epd-query`; the aggregate
skill is `environmental-data-query`. Skill titles use Data Querying. Only the
aggregate declares roles: `data-searcher`, `data-matcher` and `data-reviewer`.
Names do not add business capabilities or change database rights.

HiQLCD and HiQLCD-AL retain their official database names. CESI's external
plugin/program ID is `cesi`; its service source code remains `hiq-cesi`.

## Runtime and authorization

The business commands are `search` and `lookup`. Search finds candidates through
the existing intelligent-query service; lookup retrieves authorized details
using the service's opaque keys. Supporting commands provide help, version,
program information, authentication, diagnostics and source metadata.

Each database program embeds its source boundary. EPD embeds its publisher set.
The aggregate embeds a closed background-source and publisher set. Renaming a
binary, adjacent configuration or a remote source-directory addition cannot
expand those sets. Source conflicts and cross-source responses are errors.

Server authorization and source terms remain authoritative. All programs retain
the data client's existing product identity and credential location. Compiled
scope neither grants a license nor narrows the OAuth token. Access failures do
not authorize switching accounts, sources or products.

Default output is a candidate preview with coverage information. `--full` means
the complete current response, not the entire database. Skills may compare
returned candidates but do not expose database-wide statistics or invent totals.

## Installation and migration

Every platform archive retains its manifest, binary, LICENSE and NOTICE.
Installers verify pinned hashes and retain complete versioned releases. An
existing entry may be replaced only when its managed origin and scope can be
established. Unrelated files, directories, external links and unverifiable
entries are preserved and reported as conflicts. Installers do not execute an
unknown same-name program to identify it.

0.7.5 replaces the former plugin, skill and role IDs. The current catalog has no
legacy aliases or duplicate release matrix. Users explicitly install the new
plugin IDs through their host and remove old subscriptions through that host.
No migration automatically deletes programs, credentials or user data. Older
immutable releases are not rewritten. See [installation](INSTALLATION.md).

## Verification and release boundaries

[Compatibility](COMPATIBILITY.md) separates native packaging, installer execution,
host discovery and business-query evidence. A successful build or native version
check does not establish authenticated database access, professional suitability
or acceptance on every host.

This publication does not release Desktop, switch its production catalog, change
the query services, purchase data, write business records or notify users.
Execution and remaining product acceptance are tracked in the
[product Feature](https://github.com/HiQ-AI/environmental-data/issues/1).
