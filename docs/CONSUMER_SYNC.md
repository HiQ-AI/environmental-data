# Automatic consumer synchronization

This market checks its registered public consumer feed every hour at minute 17
and supports a manual `Synchronize published consumers` run. It updates complete
plugin packages and exact CLI pins through one normal pull request. Automatic
merge is disabled; reviewing and merging remains separate from discovering an
update. Updating the market does not upgrade a user's installed CLI or restart a
session.

`consumer-sources.json` explicitly registers the `two-products` channel, exactly
`environmental-data` and `epd-data`, allowed archive prefixes and the
`cli-release.json` root file. The retired `published` twenty-plugin feed cannot
be accepted or restore single-database directories. `consumer-lock.json` records
accepted consumer sequence, producer revision and bundle digest. The initial
reviewed two-product migration replaces the old registration; no accepted old
lock existed on its base main. New lock entries come only from the validated
new-channel pointer. The producer publishes an immutable public bundle first and updates its short-cache discovery pointer last. Consumer package
versions are independent of the CLI version, so Environmental Data skills can be
updated without rebuilding unchanged native programs.

The synchronization script verifies identity, channel, SHA256, safe paths,
immutable revision and nondecreasing CLI versions. The sealed root projection's
product IDs, domain protocols and CLI pins must match the consumer entries.
Complete source updates are
staged and checked with the existing catalog generator before replacing current
files. Downloaded scripts are not run. A bad feed preserves the existing source;
independent valid feeds may still produce an update. An unchanged feed produces
no empty commit or new PR.

The bot uses this repository's GITHUB_TOKEN only. Because token-created PR events
do not start normal PR CI, it explicitly dispatches the existing static validation
workflow on the exact pushed head. Validation checks that head before and after
running the catalog check. No synthetic successful status or bypass is used. The
workflow neither approves nor merges PRs. If repository policy denies PR creation,
the pushed automation branch is retained and reused on the next run; no personal
or cross-repository token is substituted. Actual PR creation remains blocked by
the organization's Actions policy: changing the repository switch returned HTTP
409. Scheduling and feed validation are deployed; the bot PR/exact-head workflow
chain is not accepted as complete until a real permitted run succeeds.

For recovery, inspect the workflow summary and producer release. Fix the producer
and publish a new valid consumer revision rather than rewriting immutable bytes
or deleting lock entries. Retain source/channel boundaries during rollback; a CLI
downgrade requires a deliberate reviewed change outside automatic synchronization.

The producer implementation and authority are maintained in
[HiQ-AI/cortex](https://github.com/HiQ-AI/cortex/blob/main/docs/PUBLIC_CONSUMER_SYNC.md).
This repository carries only reviewed consumer tooling and public packages.
