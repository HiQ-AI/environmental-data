# Prepare environmental-data and continue the query

Expected CLI: environmental-data 0.7.5. This package's installation.json pins the exact archive, installer and SHA256 for each platform. Native plugin installation installs instructions, not necessarily a binary.

1. Discover the command with command -v environmental-data (POSIX) or Get-Command environmental-data (PowerShell). Also consider the normal per-user entry: $HOME/.local/bin/environmental-data or $env:LOCALAPPDATA/Programs/EnvironmentalData/bin/environmental-data.exe.
2. Before executing an existing entry, establish ownership from the managed versioned manifest, binary SHA256 and source/publisher scope. Never execute an unknown same-name program to identify it. Preserve unrelated entries; use independent install/bin directories and the verified absolute path when ownership is unknown.
3. If missing/outdated, read installation.json; select this OS/architecture and download the pinned installer into a new empty directory. Verify its full SHA256 using shasum -a 256 / sha256sum or Get-FileHash -Algorithm SHA256. Read the verified script before execution. From outside the download directory run sh <absolute-script-path> or powershell.exe -NoProfile -File <absolute-script-path>. Do not pipe downloads into a shell or change execution policy. Windows 0.7.5 automated installer extraction has a known failure; if encountered, report it rather than claiming installation or weakening security. An available verified native archive can be installed manually only within host permissions, retaining manifest, LICENSE, NOTICE and bin together.
4. Use the host's existing permissions; request only a genuinely necessary approval. Do not change global profiles, credentials or another application's settings. Use the same trusted absolute path throughout, or add only its verified directory to this session's PATH. Execute version and info --json and compare the program/version/scope to installation.json; then read search --help and lookup --help.
5. Complete authentication below when required, then continue the pending original request. Do not substitute a webpage factor for a failed CLI query.

## Sign in and resume the query

Use the same trusted executable throughout preparation, login and query. Substitute its verified absolute path for the bare command in every example if using an independent install directory.

```bash
environmental-data doctor
```

Doctor always prints JSON. Exit 0 means a local credential was found; exit 2 means none was found. It does not validate current server authorization. Already authorized requests do not need another login. Background search and lookup require this product’s normal authentication.

When the requested operation requires authentication and credentials are missing or the endpoint explicitly rejects the credential, actively start one login task:

```bash
environmental-data login --json
```

The CLI does not open a browser and has no --no-browser switch. --json does not return immediately: QR, authorization URL, user code and waiting text appear on stderr; stdout is reserved for final success JSON. Capture both streams. Retain the host task/process ID and the pending query, source/model/kind and exact lookup keys.

Extract the actual authorization URL from this process. If the host has an available, authorized capability to open the user's normal browser, use it. Also present a clickable Markdown link, for example [Open the authorization page](<ACTUAL_URL_FROM_THIS_LOGIN>), replacing the placeholder with the actual returned URL, plus the real user code. If opening fails or is unavailable, the clickable link is the continuation path; do not leave only a code-block URL or ask the user to copy it. Do not guess URLs or hard-code a host tool name. Do not use an isolated automation browser without the user's login state as a substitute for their browser. The user personally approves the data-client device authorization; do not approve or sign in on their behalf. This is not an official Claude login.

The current CLI does not display expiry duration; do not invent a countdown. Preserve an expiry only if actually returned. Never disclose device codes, access tokens or credential contents, and never ask the user to paste a token.

### Own the wait and resume

The login process already polls the authorization service until approval or its expiry deadline. Use the host's existing background-task notification or bounded task-result wait; do not implement another OAuth client, cron, credential watcher or repeated doctor loop. Keep one pending process. If a task appears lost, inspect that original task before starting anything new.

After the original process exits 0 with final {ok:true}, run doctor once to confirm local preparation and resume the original search/lookup through the same executable. The query's actual response establishes service access, not doctor or the user's message saying approval is done. Do not stop at “login succeeded”. If the host cannot wake across turns, state the actual waiting state and how this task will be resumed; do not claim automatic continuation without a mechanism.

On timeout/expiry, denial or network failure, report the actual error and keep the request. A new login is appropriate only after the previous attempt has ended and the failure/user action warrants retry; never restart indefinitely. A successful query with restricted values is an entitlement decision, not a reason to log in repeatedly, change accounts or purchase access. Keep credentials in this product's existing store; never read/copy tokens from Desktop, Claude or another client.

