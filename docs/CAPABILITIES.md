# Capabilities and boundaries

Environmental Data is a multi-source environmental-data discovery and matching tool. Use it in the workflow you choose: research, comparisons, reporting, procurement, assessment or downstream analysis. Its current connector's process-dataset format and service coverage do not restrict the user's purpose to LCA.

## Current connector

Search published process datasets; constrain source/version/system model when needed; inspect references and available metadata; retrieve authorized numerical results; propose matches, proxies or unresolved needs while preserving input identity. Discover actual command inputs with the installed CLI's help and schemas rather than guessing fields.

The [source inventory](../plugins/querying-lca-datasets-expert/SOURCES.md) distinguishes source availability, numerical-data access, LCIA coverage and applicability. Directory membership alone does not establish any account's rights or a successful lookup for every dataset. New databases are not connected by a name change. The separate published-EPD query plugin uses the existing declaration API; it is not an audit expert. Retain declaration publisher, unit, method/module, validity and restrictions separately from background source/version/model coordinates.

## Using a result

Retain source, version, system model, dataset identity, reference product/unit, geography, available reference period/technology evidence, indicator/method and source link. Compare those against the question before selecting. A database release year is not the dataset's reference year. Explain uncertainty and do not invent missing factors, silently substitute databases or call an identity check a quality judgment.

## Permissions and input

Use the intended account and its existing CLI login/controlled credentials. Never request secrets in chat or borrow another application's tokens. Do not redirect authenticated requests to another endpoint to evade entitlement restrictions.

Read only authorized inputs and send only the necessary query fields. An arbitrary workbook is not automatically a supported bulk upload. Preserve original files and keep sensitive material out of public issue reports.

## Effects and exclusions

Data retrieval and proposed matching do not write to a model, bind datasets, import records, calculate impacts, run an EPD review, notify people or certify a result. Those are separate tools/actions with their own authorization.

Search and upstream processing may use service capabilities; do not promise cost-free or offline operation. Inspect actual errors and receipts, respect host permissions, and do not disguise failed access as an empty source. Agent roles are operating guidance, not backend ACLs.

Spreadsheet editing is a separate optional host capability. No general Office/PDF skills, licensed databases, CLI binaries, credentials or customer data are stored in this repository.

## Source-specific entrypoints

Single-source plugins use independent executables with a compiled source boundary, which rejects source
conflicts, cross-source output and tools without a verifiable source contract.
Opaque-key lookup/statistics/hotspot remain aggregate capabilities rather than
guessed source-specific operations. The aggregate is selected explicitly, not as
a recovery route after denied access. Compiled scope is not an OS shell sandbox or a narrower OAuth token. The aggregate also has a fixed supported-source/publisher set; remote additions cannot expand it.
Public metadata and EPD search are intentionally read-only public endpoints;
other queries retain their existing authentication. See [distribution](DISTRIBUTION.md).
