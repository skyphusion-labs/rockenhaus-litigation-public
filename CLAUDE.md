# CLAUDE.md

Guidance for agents working in the **public** Rockenhaus litigation site repo.

## What this is

**Public, CC0** filed/served court-record site. Live at **[rockenhaus.net](https://rockenhaus.net/)**
(alias `litigation.rockenhaus.net`, same site). Maintained pro se by Conrad Alan Rockenhaus.
GitHub: `skyphusion-labs/rockenhaus-litigation-public` (public; crew-accessible).

This is **not** the private litigation repo. The private source of truth is
`rockenhaus-litigation` (markdown, evidence, privileged `work_product/`).

## Hard boundaries

- **Filed/served PDFs and public hub content only.** Nothing privileged belongs here.
- **NEVER copy from private `work_product/`** (or any privileged strategy, session commits, drafts
  not filed/served) into this repo or anywhere external.
- **Publish gate is manual and human-reviewed.** Private CI may render PDFs; handoff into *this*
  repo is never auto-opened from private CI. PR here -> required status checks `ci` and
  `coverage` (org ruleset `aviation-grade-main-org`; that ruleset also applies CodeQL code
  scanning) -> merge to `main` -> deploy.
- **Metadata names the CASE, not people as the product.** Filenames, slugs, and SEO framing are
  case-centric court-record surfaces, not a people-dossier product.
- **Crew may work this public repo.** They must not pull private privilege into it. There is
  no ME-ONLY wall on the private repo either (retired 2026-09-25). Both repos are ordinary
  work. The privilege rule is separate and still absolute: never copy private `work_product/`
  into this repo.
- **No em-dashes (U+2014) or en-dashes (U+2013)** in source, copy, or docs. Use commas, semicolons,
  parentheses, or `--`.

## Publish model (summary)

1. Private repo builds/holds sources and evidence.
2. Human PII / privilege review before any PDF is copied here.
3. PR on this repo; required checks; merge to `main`.
4. Deploy (`.github/workflows/cloudflare-pages.yml`, `ubuntu-24.04`, Cloudflare Pages project
   `rockenhaus-litigation`), IndexNow (`scripts/indexnow_ping.py`), cache purge of
   `rockenhaus.net`, `www.rockenhaus.net`, and `litigation.rockenhaus.net`
   (`scripts/cloudflare_purge_cache.py`).

Ops detail: `docs/ops/publish-runbook.md`, `docs/ops/publish-matrix.md`, README.

## Do not put here

- Privileged case strategy, mental impressions, or unfiled drafts from private `work_product/`.
- Private evidence dumps that were never filed/served.
- Anything that would make this site a back-channel for the private repo.

## Commits

Conventional Commits (`docs:`, `feat:`, `fix:`, `ci:`). Author on Conrad's laptop:
`Conrad Rockenhaus <conrad@skyphusion.org>`. PR workflow; do not force-push `main`.
