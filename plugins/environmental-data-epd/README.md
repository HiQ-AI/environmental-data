# Published EPD Data

Search actual published Environmental Product Declarations, not the EPD audit
expert. Publishers belong to a declaration database separate from background
process sources; no invented background-source ID is used.

```text
/plugin install environmental-data-epd@environmental-data
```

Prepare shared CLI **0.6.0** separately. Query with
`querying-lca-datasets scoped epd epd-search --query concrete --limit 5 --json`.
This uses the existing public read-only declaration API. Local login is not
required for this endpoint; server restrictions and publisher terms still apply.
The complete envelope preserves publisher, unit, indicator/method/module,
restricted markers, validity, metadata and page cursor. Missing values are not
zero, public metadata is not a data redistribution license, and one successful
query does not establish coverage or professional suitability for all products.

Do not substitute product declarations for background processes without explaining
the functional-unit and boundary differences. This plugin neither audits nor
certifies an EPD or calculates a product footprint. See
[installation](../../docs/INSTALLATION.md) and [evidence](../../docs/DISTRIBUTION.md).
