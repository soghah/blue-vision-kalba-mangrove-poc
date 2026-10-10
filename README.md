# Blue Vision — Kalba Mangrove Monitoring

Proof of Concept for the Arab Youth Space Hackathon: 813 Challenge.

Blue Vision combines open Sentinel-2 monitoring with targeted EnMAP hyperspectral diagnosis to screen coastal vegetation change in Kalba, UAE, and prioritise locations for closer imagery review or field inspection.

## Key results

- Sentinel-2 coastal vegetation proxy: **112.36 ha in 2016** and **97.24 ha in 2025**.
- Endpoint proxy change: **−15.12 ha (−13.5%)**.
- Ten-year linear trend: **−1.49 ha/year**, but not statistically significant (**p = 0.184; R² = 0.209**).
- ESA WorldCover 2021 reference-map agreement: **precision 0.720, recall 0.822, F1 0.768, IoU 0.623**.
- EnMAP screening: **900 valid coastal-vegetation pixels**; **177** were in the lowest 10% of at least one hyperspectral indicator and **3 pixels (~0.27 ha)** were in the lowest 10% of both.

These are screening results, not confirmed mangrove loss or field-validated vegetation stress.

## Repository contents

- `Blue_Vision_Kalba_Mangrove_PoC.ipynb` — public, lightweight notebook.
- `requirements.txt` — pinned Python dependencies.
- `Blue_Vision_Endpoint_Composites.png` — 2016/2025 visual comparison.
- `Blue_Vision_WorldCover_Validation.png` — independent reference-map comparison.
- `Blue_Vision_Kalba_PoC_Dashboard.png` — main six-panel decision dashboard.
- `Blue_Vision_EnMAP_Hyperspectral_Diagnostics.png` — derived hyperspectral indicators.
- `Blue_Vision_EnMAP_Follow_Up_Priority.png` — relative follow-up priority map.

## Run the open workflow

Open the notebook in Google Colab and run all cells. Sentinel-2 and ESA WorldCover data are accessed through the Microsoft Planetary Computer STAC API. No private Google Drive access or credentials are required for the open workflow.

The notebook uses the following area of interest: `[56.32, 24.96, 56.40, 25.05]` (west, south, east, north), with Sentinel-2 annual composites for February–April 2016–2025 at 20 m working resolution.

## Optional EnMAP reproduction

The original EnMAP rasters are licensed inputs and are **not redistributed** in this repository. The notebook runs safely without them and displays the derived public PNG outputs.

To recompute the EnMAP section, obtain the following scene from the official DLR EnMAP portal under the applicable licence conditions:

- **Scene ID:** `ENMAP01-____L2A-DT0000152124_20250911T072327Z_006_V010502_20250914T181224Z`
- **Acquisition date:** 11 September 2025
- **Product:** EnMAP Level-2A

Upload these three files to `/content/Blue_Vision_Data/` in the Colab session:

- `*SPECTRAL_IMAGE_COG.tiff`
- `*QL_QUALITY_CLOUD_COG.tiff`
- `*QL_QUALITY_CLASSES_COG.tiff`

Then rerun the EnMAP cells. The original GeoTIFF files must not be committed to the public repository.

## Validation and limitations

- The mapped class is a coastal vegetation screening proxy, not a confirmed mangrove boundary.
- ESA WorldCover is a satellite-derived reference map, not field ground truth.
- Tide, mixed shoreline pixels, seasonal differences, threshold sensitivity, and residual atmospheric effects may influence results.
- The EnMAP assessment uses one acquisition date; its percentile thresholds are relative screening rules, not universal stress thresholds.
- Field observations and authoritative local boundaries are required before ecological or regulatory conclusions.

## Data and attribution

- Contains modified Copernicus Sentinel data (2016–2025), accessed through the Microsoft Planetary Computer.
- Contains modified ESA WorldCover 2021 data.
- Contains modified EnMAP data ©DLR 2025.

## Submission note

The fully executed notebook with embedded outputs is supplied separately in the optional supporting archive. The public notebook is intentionally lightweight so GitHub can render it reliably.
