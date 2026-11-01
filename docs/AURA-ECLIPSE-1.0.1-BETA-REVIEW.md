# Aura Eclipse 1.0.1-beta — review of supplied source archives

Reviewed three actual ZIP uploads on 2026-11-01:

| Candidate | ID / version | Findings | Decision |
| --- | --- | --- | --- |
| addon-bridge | `codeberg.kotazi_dev.addonbridge` / 1.0.9 | Standalone Myspoti HTTP-addon bridge; manual-only configuration, empty source catalogue; requires user-provided compatible HTTPS endpoint and tests manifest/search/stream/media headers. | Reuse architecture for optional manual-source mode, **not** as an automatic new provider. |
| mornye-download-integration | `codeberg.kotazi_dev.lossless` / 2.0.1 | Separate extension, with its own download/session/pairing code. | Do not merge its code into Milestone without compatibility, rights and live tests. |
| ArchiveTune Sources by Mauro | `group.natune.archivetune.sources` / 1.2.0 | Separate Myspoti extension; multiple resolvers including NetEase/JioSaavn/QQMusic and optional account/server-dependent sources. README also describes embedded Qobuz credentials, OAuth, optional pool keys and decryption. | Review individual zero-config resolvers and license first. No automatic merging, no private-key extraction or protected-content bypass. |

## Important limitation
These three ZIPs are **not** Aura Eclipse 1.0.1 and are not a ready-to-merge set of new servers. The bridge explicitly ships `catalog/catalog.json` with `sources: []`. Shipping it without a user-supplied authorized endpoint would add no playback source.

## Beta gate
Keep Aura Eclipse 1.0.0 Milestone unchanged. A beta must include an actual, isolated runtime change, a validated ZIP, and regression checks before it can be called test-ready. Avoid silently replacing the stable package with another project's manifest or extension ID.
