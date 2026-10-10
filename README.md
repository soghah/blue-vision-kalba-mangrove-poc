# Reproducible input data

This repository does not redistribute full satellite scenes. The main notebook retrieves the open inputs directly from the Microsoft Planetary Computer STAC API.

## Sentinel-2 input parameters

- Collection: `sentinel-2-l2a`
- Area of Interest: `[56.32, 24.96, 56.40, 25.05]` in EPSG:4326
- Study period: 2016-2025
- Seasonal window: 1 February to 30 April
- Scene-level cloud-cover filter: less than 20%
- Maximum selected observations: six lowest-cloud observations per year
- Bands: `B02`, `B03`, `B04`, `B08`, `B11`, and `SCL`
- Working resolution: 20 m
- Composite: annual median after Scene Classification Layer masking

## ESA WorldCover input

- Collection: `esa-worldcover`
- Product year: 2021
- Reference class: mangrove class
- Access: Microsoft Planetary Computer STAC API

## Optional EnMAP input

- Product: EnMAP Level-2A
- Acquisition date: 11 September 2025
- Scene ID: `ENMAP01-____L2A-DT0000152124_20250911T072327Z_006_V010502_20250914T181224Z`

The original licensed EnMAP rasters are not committed. To recompute the optional section, obtain the scene from the official DLR EnMAP portal and place the following files in `data/enmap_optional/`:

- `*SPECTRAL_IMAGE_COG.tiff`
- `*QL_QUALITY_CLOUD_COG.tiff`
- `*QL_QUALITY_CLASSES_COG.tiff`

If these files are absent, the notebook skips EnMAP raster calculations without failing. The derived example figures remain available in `results/`.
