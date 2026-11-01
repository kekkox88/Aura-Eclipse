# Aura Eclipse 1.0.1-beta — source evaluation plan

Baseline: **Aura Eclipse 1.0.0 — Milestone**. Keep the stable extension ZIP unchanged. This document does not claim a working new provider.

## Non-negotiable requirements
- No personal API keys, manually entered private tokens, or credential scraping.
- No hard-coded unofficial endpoints assumed to be permanent or guaranteed to provide lossless audio.
- No bypass of DRM, authentication, access controls, or paid-service restrictions.
- Keep current working source order, Qobuz/Tidal logic, and Deezer Eclipse UltraMAX behavior unchanged until isolated tests pass.
- No public APK, release, or changes to `main` as part of this evaluation.

## Candidate codebases
- ArchiveTune (Mauro): review each resolver and license; verify protocol and permissions before porting.
- https://codeberg.org/kotazi-dev/addon-bridge: examine whether server pool, health checks, and fallback are reusable independently of service-specific endpoints.
- https://codeberg.org/kotazi-dev/mornye-download-integration: examine interfaces and licensing only; do not import protected-content decryption or authorization bypass logic.

**Status:** source archives have not yet been retrieved and inspected in this work session. No integration is approved or implemented.

## Proposed isolated bridge abstraction
- Define provider descriptors: id, supported actions, declared public endpoints, provenance and licensing.
- Use bounded timeouts and capped retries; avoid infinite retry loops or source storms on mobile data.
- Distinguish transport failure, not found, rate limit, authorization required, and invalid media.
- Reject untrusted redirects or non-HTTPS endpoints by default.
- Preserve verified content type and container/codec metadata; never relabel lossy audio as FLAC.
- Require explicit user approval for any new network permission or account linkage.
- Add test fixtures for offline, slow 4G, captive portal, expired URLs, and multiple fallback failures.

## Gate before writing runtime code
1. Obtain and inspect the actual source and licenses of all three candidates.
2. Identify a public, authorized, stable endpoint that needs no personal credentials.
3. Verify real stream resolution and format on test cases.
4. Implement in a separate 1.0.1-beta extension artifact; do not overwrite the Milestone.
5. Run automated tests and mobile-network playback tests before promoting anything.
