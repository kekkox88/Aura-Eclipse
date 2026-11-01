# Aura Eclipse
Personalized fork of [kota-zo/myspoti](https://github.com/kota-zo/myspoti). Preserve original GPL license and upstream credits.

## Workflow policy
- Android CI: test and compile only; never upload or publish APKs.
- Upstream sync: propose changes by pull request, no automatic merge.
- Signing: manual workflow requiring repository secrets; APK stays on ephemeral runner, not uploaded.
- No GitHub Releases, tags or deployments are created by these workflows.
- Secrets: AURA_ECLIPSE_KEYSTORE_BASE64, AURA_ECLIPSE_KEYSTORE_PASSWORD, AURA_ECLIPSE_KEY_ALIAS, AURA_ECLIPSE_KEY_PASSWORD.

## Bundled addon
Aura Eclipse 1.0.0 — Milestone is planned as a preinstalled extension. Its exact package and the upstream extension registration API must be verified before integration. Do not replace or reconstruct the tested addon from memory.
