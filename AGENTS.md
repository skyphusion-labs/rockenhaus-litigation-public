# Rockenhaus litigation

This file is the guide for any coding agent and any contributor. Follow it.

## What this project is

This repo is the public court-record site. The license is CC0. It holds filed and served records only. The live site is [rockenhaus.net](https://rockenhaus.net/). The alias `litigation.rockenhaus.net` is the same site. Conrad Alan Rockenhaus maintains it pro se.

The GitHub repo is `skyphusion-labs/rockenhaus-litigation-public`.

This is not the private litigation repo. The private source of truth is `rockenhaus-litigation`. That repo holds markdown, evidence, and privileged `work_product/`.

## Hard boundaries

Put filed and served PDFs here. Put public hub content here. Nothing privileged belongs here.

Never copy private `work_product/` into this repo. Never copy it anywhere else. That ban covers privileged strategy. It covers session commits. It covers a draft that nobody has filed or served.

A human reviews every handoff. Private CI may render PDFs. Private CI must not open a pull request in this repo.

A pull request needs the checks `ci` and `coverage`. Code scanning runs on the pull request. A merge to `main` deploys.

Metadata names the case. Filenames, slugs, and SEO stay case-centric. Do not frame them as a dossier of people.

The privilege rule stays absolute. Never copy private `work_product/` into this repo.

Do not use an em dash (U+2014) or an en dash (U+2013) in source, copy, or docs. Use a comma, parentheses, or two hyphens (`--`).

## Publish model

Read [docs/ops/publish-runbook.md](docs/ops/publish-runbook.md). Read [docs/ops/publish-matrix.md](docs/ops/publish-matrix.md). Read [README.md](README.md).

1. The private repo builds sources and holds evidence.
2. A human reviews personal data and privilege before anyone copies a PDF here.
3. Open a pull request on this repo. Wait for the required checks. Merge to `main`.
4. Deploy uses [.github/workflows/cloudflare-pages.yml](.github/workflows/cloudflare-pages.yml) on `ubuntu-24.04`. The Pages project is `rockenhaus-litigation`.

[scripts/indexnow_ping.py](scripts/indexnow_ping.py) pings IndexNow after deploy. [scripts/cloudflare_purge_cache.py](scripts/cloudflare_purge_cache.py) purges cache for three hostnames. Those hostnames are `rockenhaus.net`, `www.rockenhaus.net`, and `litigation.rockenhaus.net`.

## Do not put here

Do not put privileged case strategy here. Do not put mental impressions here. Do not put an unfiled draft from private `work_product/` here. Do not put private evidence that nobody filed or served. Do not use this site as a back channel for the private repo.

## Docs

Write Simplified Technical English. Use short sentences. Put one idea in each sentence. Use the active present tense. Use plain words. Use the same word every time.

State the limit next to the capability. Do not turn a measured result into a promise.

## Commits

Use Conventional Commits (`docs:`, `feat:`, `fix:`, `ci:`). Use a pull request. Do not force-push `main`.

## Safety

Do not put a secret in a tracked file. Do not put a secret in a log. Do not put a secret in an issue. Do not put privileged `work_product/` in this repo.
