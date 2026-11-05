# Capabilities and boundaries

## Environmental data queries

Use Environmental Data to find candidates for research, comparisons,
procurement, reporting, assessment or another authorized workflow. The supported
operations are requirement clarification, candidate search, applicability
comparison, proposed matching and authorized detail retrieval.

`search` accepts the user's complete query. Source/version and system-model
selectors apply where the selected program supports them. Geography, technology,
time and functional requirements belong in the query and must be checked against
returned evidence. `lookup` accepts exact opaque keys returned by the service;
keys must not be decoded, synthesized or edited.

Default output is a preview with partial/omitted coverage information. `--full`
returns all of the current response, not a complete database inventory. Continue
with a cursor only where the command actually provides one. Empty search means
no match for that request; restricted data is a separate access state.

The skills do not provide a database-wide grouping, median, statistics or hotspot
API. A calculation over retrieved candidates must identify its finite sample and
must not be described as a whole-database or industry statistic.

## Source and declaration scope

`environmental-data` is the single background-database program. It embeds a
closed source set and accepts one or several supported databases through
`--sources`. Unknown sources and out-of-scope response identities are errors.
`epd-data` is the separate published-declaration program. Neither program can
cross its business domain or serve as a fallback after denied access. Remote
source-directory changes cannot expand either compiled set.

The [source inventory](../plugins/environmental-data/SOURCES.md) distinguishes
published availability, advertised numerical coverage and access flags. A source
listing is not a completed lookup or a statement of the current account's rights.

Published EPD declarations use the existing separate query service. Preserve
publisher, declaration identity, declared unit, method/module, validity and
restrictions. A declaration is not automatically interchangeable with a
background process dataset. These plugins do not perform EPD audit or certification.

## Applying results

Keep source, version, system model, record identity, reference product/unit,
geography, available time/technology evidence, method/indicator and source link
with each candidate. Compare these with the user's requirements before selecting
or proposing a proxy. A database release year is not the data's reference year.
A matching name or valid key does not establish suitability.

Preserve original input row identities during list matching. Explain proxies,
unresolved requirements, missing factors and access restrictions. Do not silently
switch sources or models, invent numerical values or treat restricted results as
an empty database.

## Permissions and side effects

Read only authorized inputs and send the minimum fields needed for the query.
An arbitrary workbook is not a supported bulk upload. Keep original materials
intact and private inputs out of public issue reports.

Use the intended account's existing CLI authentication. Never request secrets in
chat, borrow another application's tokens or redirect authenticated requests to
evade entitlements. Compiled scope does not grant a database license, narrow the
OAuth token or create an OS sandbox. Source terms remain applicable.

Queries may use upstream service capabilities; no offline or cost-free guarantee
is made. Respect actual errors and host permission decisions. Search and proposed
matching do not import data, bind records, edit models, calculate a footprint,
submit business records, purchase access, notify people or certify results.

Spreadsheet editing is a separate optional [capability](SPREADSHEETS.md). General
Office/PDF skills, licensed databases, CLI binaries, credentials and customer data
are not bundled here. See [distribution](DISTRIBUTION.md) and
[installation](INSTALLATION.md) for program preparation and migration.
