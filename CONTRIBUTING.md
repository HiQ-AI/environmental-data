# Catalog maintenance

## Ownership

The private producer owns the channel declaration, program scope, consumer-name
mapping and executable builds. Its sealed index is copied without modification
to `cli-release.json`. The public repository owns the published plugin content,
host integration and user documentation. Do not copy private implementation code
or create another editable source list.

`marketplace.json` is the typed consumer catalog. Its CLI entries must match the
sealed release exactly. `.claude-plugin/marketplace.json` and the marked README
catalog are generated projections:

```bash
npm run generate
```

```bash
npm test
```

No dependency installation is required for these checks.

## Names and components

The active set is exactly `environmental-data` and `epd-data`; plugin ID and CLI
name are identical. The database skill is `environmental-data-query`, and the
published-declaration skill is `epd-query`. Only the database product declares
`data-searcher`, `data-matcher` and `data-reviewer`. Do not restore retired
single-database entries or an EPD domain inside the database program.

A naming change must update IDs, directories, manifests, skill frontmatter,
component references, installation metadata and both catalog formats together.
Document the user migration explicitly. Do not leave legacy aliases or duplicate
active entries. Database service source codes and account identity must not
change merely because a public name changes.

## Release updates

Use a feature branch and PR. Generate consumer content from the producer's
matching declaration and actual sealed release, then update the catalog and
native projection. Preserve immutable release URLs and full digests. Never
rewrite an existing version's artifacts or replace real release metadata with a
fixture. Version-specific evidence must identify its source revision and limits.

Write current installation, capability and distribution documents as complete
instructions for the current version. Keep historical facts in their versioned
release record or Git history, not as contradictory current instructions.
Descriptions must list supported capabilities and preserve access, coverage,
input and side-effect boundaries.

## Verification and safety

Run the catalog checks and validate changed native manifests using the host's
validator. Exercise affected host discovery or installation paths when IDs or
layout change. Changed artifacts require full-digest and actual platform/version
verification before execution. Packaging, host discovery and authenticated
business queries are separate evidence.

Hosted CI performs static checks only with read-only permissions. Do not add
business, model, database, browser or native-runtime integration tests to it.
Never commit credentials, customer inputs, downloaded binaries or restricted
third-party skills. Preserve applicable publisher and database terms.

This repository does not switch Desktop production routing, publish Desktop or
authorize another service deployment. Report reproducible issues with the actual
platform, plugin/CLI version and redacted evidence.
