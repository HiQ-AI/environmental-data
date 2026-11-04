# Contributing

This repository is the authoritative source for the Environmental Data plugin's metadata, roles, guides and CLI supply pins. Do not maintain a separate editable copy in another marketplace.

The root `marketplace.json` owns identities, versions, component inventory and CLI supply metadata. The native `.claude-plugin/marketplace.json` and marked README plugin index are generated projections:

```bash
npm run generate
```

```bash
npm test
```

Use a feature branch and PR. Preserve the stable plugin ID, CLI command/authentication and existing release pins unless a scoped change explicitly requires a compatible migration. Keep the public product name in supported `displayName` fields and the Cortex catalog's human-readable name, not in a renamed technical ID. Do not freeze the current inventory count into long-term positioning.

Update the actual plugin guides when capabilities, access, dependencies or side effects change. Describe current published sources and coverage accurately; new branding does not integrate a new database. Database-specific product packaging is not implied by this repository's name or directory layout.

Validate native marketplace/plugin manifests with the available host validator after schema changes. For changed archives, verify full digests and actual platform/version before execution. Hosted CI performs static checks only, using GitHub-hosted runners with read-only permissions: no business/model/database/browser/native-runtime integration tests, deployment workflow or internal self-hosted runner.

Never commit credentials, customer inputs, downloaded binaries or restricted third-party Office/PDF skills. Preserve applicable publisher/database terms. Report issues with redacted evidence, actual OS/architecture and plugin/CLI versions.

This repository does not switch Desktop production routing or publish Desktop. Do not broaden a plugin change into another host or service deployment.

## Native CLI release projection

The private producer owns source/channel declarations and executable builds.
After actual release verification, copy the exact sealed producer index into
`cli-release.json`, update each catalog CLI from its matching plugin entry, and
update operating instructions for that compiled executable. Do not hand-maintain
a second source list or reintroduce a shared CLI/scoped selector. Record the
original index SHA256 and native verification scope in distribution evidence.
Run `npm run generate` and `npm test`; no dependency installation is needed.
Native host installation and business-query evidence remain distinct.
