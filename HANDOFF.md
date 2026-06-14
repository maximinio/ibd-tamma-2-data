# IBD TaMMA 2 webapp data bundle handoff

Last updated: 2026-06-14

## Stable paths and repo

- Local bundle path: `/mnt/HDD2/ibd_tamma_2/webapp_ibd_tamma_2`
- Git repo: `https://github.com/maximinio/ibd-tamma-2-data`
- Manifest: `/mnt/HDD2/ibd_tamma_2/webapp_ibd_tamma_2/manifest.json`
- Generic app code: `/home/lmassimino/Documents/scripts/codex/webapp_rna_seq`
- Public app: `https://ibdtamma.lucamassimino.com/`

## Bundle purpose

This repository is the project-specific static data layer for the reusable RNA-seq Shiny webapp. It should contain data, metadata, indices, and branding assets, not reusable app logic.

The webapp should be able to read the bundle through `manifest.json`, whether served locally, through GitHub/static URLs, or another static host.

## Current host layer

Key files/directories:

- `metadata/metadata.tsv.gz`
- `host/umap/host_umap_coordinates.tsv.gz`
- `host/db/dge/*.sqlite.gz`
- `host/db/pathways/*.sqlite.gz`
- `indices/host_contrasts.tsv`
- `assets/branding/*`
- `visual_qa/*`

The current app starts with host-layer outputs:

- metadata Sankey;
- Human UMAP;
- DGE volcano;
- GO BP dotplot;
- expression violins;
- top druggable DEG/OpenTargets panel.

Microbiome and functional layers can be added later by extending the manifest and app modules rather than changing the host bundle layout.

## Data format choices

- DGE and pathway data are SQLite compressed as `.sqlite.gz`.
- No TSV/RDS fallback should be used for DGE/pathway data.
- Metadata remains compressed TSV because it is small enough and useful for display/filtering.
- UMAP coordinates remain compressed TSV for lightweight loading.
- Large future matrices should be represented by indexed, queryable formats rather than loaded wholesale into Shiny memory.

## Branding

The TaMMA 2 logo used in the app should be high resolution, transparent-background, and readable on a dark app theme. Avoid white boxes or overscaled raster assets.

The current conceptual logo language:

- intestine-centered;
- transcriptome/microbiome/metabolism layers;
- target prioritization as downstream integration;
- no OpenTargets as an intestine-derived layer because OpenTargets comes from web/public evidence.

## QA and publishing

Visual QA outputs are stored in:

- `/mnt/HDD2/ibd_tamma_2/webapp_ibd_tamma_2/visual_qa`

After data bundle changes:

- rebuild `manifest.json` if paths/checksums changed;
- commit and push the data bundle repo;
- redeploy or refresh the Heroku app only when app config/code changed;
- rerun visual QA against `https://ibdtamma.lucamassimino.com/`.

## Design guardrails

- Keep the data bundle project-specific.
- Keep reusable plotting/app behavior in `webapp_rna_seq`.
- Do not add local-only absolute paths to `manifest.json`.
- Prefer relative paths in the manifest.
- Make missing data fail visibly rather than falling back to stale files.
