# IBD TaMMA 2 data bundle

Static data bundle for the plug-and-play RNA-seq Shiny web application.

The app entry point is `manifest.json`. Paths in the manifest are relative so the same bundle can be served from GitHub raw URLs, local disk, or another static file host.

Current host layer layout:

- `metadata/metadata.tsv.gz`
- `host/umap/host_umap_coordinates.tsv.gz`
- `host/db/dge/*.sqlite.gz`
- `host/db/pathways/*.sqlite.gz`
- `indices/host_contrasts.tsv`
- `assets/branding/*`

DGE and pathway data are SQLite-only. The application intentionally does not fall back to local TSV/RDS result tables.
