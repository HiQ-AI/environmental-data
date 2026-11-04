# Compatibility and verification

## Hosts

- **Claude Code:** native marketplace/plugin manifests are strictly validated with Claude Code2.1.317. Marketplace addition and plugin installation are exercised in an isolated HOME/config without business credentials, model calls or CLI provisioning. A successful installation checks packaging/discovery, not data access or professional suitability.
- **Cortex Hosts:** root `marketplace.json` preserves typed CLI supply metadata. A compatible Host can provision the pinned CLI; this publication does not switch existing Desktop's production directory or release Desktop.
- **Codex/other hosts:** no marketplace adaptation or end-to-end installation verification is claimed. A host's ability to use the native CLI does not make it compatible with Claude Code's marketplace format.

## Platform pins

CLI0.5.1 has catalog entries for `darwin-arm64`, `darwin-x64`, `linux-arm64`, `linux-x64` and `win32-x64`. Plugin package0.5.3 supplies branding/guides; the CLI version, archive digests, commands and authentication are unchanged by this independent repository.

## Scope of evidence

Static checks cover declared inventory, unique stable IDs, component files/frontmatter/references, manifest versions, recognized display names, pinned HTTPS release metadata and generated marketplace/README consistency. Public source inventory is a dated anonymous metadata read, not numerical lookup acceptance or per-account authorization.

Native plugin installation does not install a business CLI or execute its workflow. No search, model call, numerical-data request, account login, database write, notification or production source change is part of this publication verification. No fresh Windows/Linux business execution matrix or full data-source acceptance is implied.

A successful manifest, install, HTTP request or CLI exit is not proof that the selected data suits the user's question. Preserve coverage/access limits and actual evidence.
