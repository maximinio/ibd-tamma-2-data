# IBD TaMMA 2 data bundle

Static data bundle for the plug-and-play RNA-seq Shiny web application.

The app entry point is `manifest.json`. Paths in the manifest are relative so the same bundle can be served from GitHub raw URLs, local disk, or another static file host.

Current host layer layout:

- `metadata/metadata.tsv.gz`
- `host/umap/host_umap_coordinates.tsv.gz`
- `host/rds/dge/*.rds`
- `host/rds/pathways/*.rds`
- `indices/host_contrasts.tsv`
- `assets/branding/*`
