# Distribution contract

## Products and artifacts

One private implementation and one channel declaration produce two programs:

| Plugin / program | Scope | Skill | Roles |
| --- | --- | --- | --- |
| environmental-data | Supported background databases, selected through --sources | environmental-data-query | data-searcher, data-matcher, data-reviewer |
| epd-data | Published EPD declarations | epd-query | None |

CLI 0.8.2 targets macOS arm64/x64, Linux arm64/x64 and Windows x64: ten native
archives. The immutable producer index is:

https://download.hiq.earth/cli/environmental-data/releases/v0.8.2/index.json

[cli-release.json](../cli-release.json) is the sealed consumer projection, not a
second editable source declaration. Its revision, scope, archive/installer hashes
and consumer names bind the catalog. Every CLI entry must match it exactly.
This repository publishes metadata, manifests, skills, roles and installation
resources, not private implementation, database content, binaries or credentials.

## Domain and authorization

The only business commands are `search` and `lookup`. Supporting commands provide
help, version, info, authentication, diagnostics and source metadata.
`environmental-data` is datasets-only; `epd-data` is declarations-only. The former
aggregate's EPD path is retired. Database source codes are unchanged, including
CESI's `hiq-cesi`. Names and installation settings do not confer rights or expand
the compiled set.

Server authorization and source terms remain authoritative. Both programs retain
the existing product identity and credential store; neither copies another
product's token or narrows the OAuth token. A public source directory or search
hit does not prove numerical entitlement. Service unavailability is not denied
entitlement. Search and lookup do not perform EPD audit, certification or business
writes. The `cortex-epd` auditing expert is a separate, unchanged product.

Default output is a received-response preview with explicit omissions. `--full`
means all of that response, not the entire database. Calculations or comparisons
must retain candidate sample limits, compatible units/methods and access evidence.
No database-wide statistics API is supplied.

## Installation and migration

Every archive retains manifest, binary, LICENSE and NOTICE. Verified installers
preserve complete versioned releases and existing credentials. Existing entries
are replaced only after managed ownership and integrity checks. Unknown files,
external links, directories and unverifiable entries remain conflicts; unknown
same-name programs are not executed to identify them.

The one-way managed migration from `environmental-data` 0.7.4/0.7.5 to 0.8.2 permits
only the exact known aggregate-to-datasets scope reduction, with unchanged dataset
sources and the known old publisher set. It does not rewrite the old manifest or
delete its payload. Other scope changes remain rejected.

The public active catalog has exactly two entries. Eighteen single-database
entries are removed without aliases or a parallel matrix. Users explicitly
replace old plugin subscriptions through their native host; no automatic deletion
of programs, credentials or user data occurs. Old immutable archives remain
unchanged. See [installation](INSTALLATION.md).

## Consumer content and synchronization

English skills and their complete local references are generated from shared
producer sources and this sealed release. Each plugin is independently usable;
no cross-plugin reference, aggregate installation or remote guide is required.
Consumer plugin versions may advance independently of CLI versions without
rewriting executable pins.

The explicit `two-products` synchronization channel accepts only these two IDs
and the registered root projection. Its validator binds CLI pins and domain scope
to that projection. The retired twenty-plugin `published` feed cannot restore old
active entries. Initial directory/registry/lock migration is a reviewed change,
not a routine feed operation. See [consumer synchronization](CONSUMER_SYNC.md).

## Evidence and release boundaries

[Compatibility](COMPATIBILITY.md) distinguishes artifact packaging, installer
execution, host discovery and real-account queries. Builds, signatures and native
version probes do not establish numerical access or professional suitability.

This publication does not release Desktop, switch its production catalog, change
billing/entitlements, purchase access, write business records or notify users.
Acceptance is tracked in the
[product Feature](https://github.com/HiQ-AI/environmental-data/issues/1).
