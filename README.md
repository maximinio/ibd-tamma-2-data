# IBD TaMMA 2 data bundle

Static data bundle for the plug-and-play RNA-seq Shiny web application.

The app entry point is `manifest.json`. Paths in the manifest are relative so the same bundle can be served from GitHub raw URLs, local disk, or another static file host.

Start here:

- `HANDOFF.md`: project-specific data contract, publishing notes, branding memory, and QA rules.
- `manifest.json`: bundle entry point consumed by the Shiny app.
- `project.yaml`: local project metadata/config used to build or inspect the bundle.
- `visual_qa/`: latest browser screenshots and metrics.

QA hygiene:

- Keep only the current intentional QA snapshot in `visual_qa/`.
- Write temporary or dated browser QA runs to `/tmp` and delete them after review.
- Do not leave `visual_qa_*` folders in this data repository.

Current host layer layout:

- `metadata/metadata.tsv.gz`
- `host/umap/host_umap_coordinates.tsv.gz`
- `host/db/dge/*.sqlite.gz`
- `host/db/pathways/*.sqlite.gz`
- `indices/host_contrasts.tsv`
- `assets/branding/*`

DGE and pathway data are SQLite-only. The application intentionally does not fall back to local TSV/RDS result tables.
