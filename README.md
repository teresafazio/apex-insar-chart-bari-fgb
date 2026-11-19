# apex-insar-chart-bari-fgb

Example configuration for the **APEx Geospatial Explorer**: clicking on an InSAR point opens a chart with its displacement time series.

**Synthetic** test data: 10 Sentinel-1 points (descending orbit) along the coastline of Bari, Italy.

## Contents

- `apex-config-fgb.json` – configuration to import into the Configuration Builder
- `data/fgb/output_descending.fgb` – mean LOS velocity (`vel`, mm/year) with the `statistics-url` attribute (FlatGeobuf, EPSG:3857, spatial index)
- `data/fgb/ts/` – cumulative LOS displacement (`disp`, mm), one FlatGeobuf per quarter, used by the time slider
- `data/csv/` – full time series of each point (277 dates, columns `date`, `disp`)
- `data/gpkg/output_descending.gpkg` – GeoPackage of the velocity layer (EPSG:4326, same fields as the original dataset), also as `output_descending.zip` for download
- `data/output_descending.geojson`, `data/ts/` – the same data in GeoJSON format (EPSG:4326)

## How the chart works

Each point has a `statistics-url` attribute containing the address of the CSV with its time series.
In the configuration, the chart uses a `lookupURL` source on the `statistics-url` field:
when a point is clicked, APEx downloads the CSV and plots it.

## Usage

1. Go to https://ge-config-builder.apex.esa.int/
2. Import `apex-config-fgb.json` into the Configuration Builder (Home → Load).
3. In the preview: *Data Values* → click on a point → *Charts* tab.

## Download

The download button in the information panel of the velocity layer serves `data/gpkg/output_descending.zip` through GitHub Pages
(`https://teresafazio.github.io/apex-insar-chart-bari-fgb/`), so that the file is delivered with the correct type.
GitHub Pages must be enabled for the repository (Settings → Pages → Deploy from a branch → `main` / root).
