# Presentation

The talk for the supervisor meeting: 21 slides, updated 28 October 2026.

| File | What it is |
|---|---|
| [swot-tank-tracker-proposal-talk.pdf](swot-tank-tracker-proposal-talk.pdf) | The slides as a PDF (2.9 MB) |
| [swot-tank-tracker-proposal-talk.pptx](swot-tank-tracker-proposal-talk.pptx) | The PowerPoint, if you want to edit it (5.0 MB) |

You can also flip through the slides on the website: <https://swot.mehara.work/presentation>. The speaker notes are kept private, so these copies have none.

## Who does what (slides 15–18)

Each of us owns one core research question from start to finish. Slide 15 gives the overview, and slides 16–18 give each member's data analysis and technical work. The same plan is on the website's Team tab: <https://swot.mehara.work/team>.

| Member | Research question | Data analysis | Technical work | Output |
|---|---|---|---|---|
| A: AI water maps | RQ1 | Label water masks with a "water under plants" class; score the maps (IoU, F1); area error against Kanhindawewa's drone survey; compare with the simple rules and SWOT's own area | U-Net (EfficientNet-B0) trained on S1S2-Water, then fine-tuned on our tanks; Sentinel-1, NISAR, Sentinel-2 and slope as inputs; a pipeline from picture day to water area | Water area for every tank on every picture day, with its accuracy |
| B: SWOT and gauges | RQ2 | SWOT minus gauge on every pass (gap and spread in cm); "good" against "suspect" readings; effect of lake size, track distance and season; how a height error becomes a volume error | Hydrocron pipeline with quality flags and an outlier test; gauge zero in metres above sea level; daily logger for the department's sheet; field visits on pass days | SWOT accuracy report, and the fixed gap for each reservoir |
| C: Storage and dashboard | RQ3, with RQ4 as a stretch | Each tank's area–height curve; storage change against the department's daily storage; tests on Kanhindawewa's drone table and against Imbulana's formula; error budget; a 2–4 week forecast against "no change" | Storage engine with thin layers and safe limits after every pass; the dashboard; automatic updates with GitHub Actions; a forecast model if time allows | Storage for every tank with safe limits, on a dashboard |

All three of us: field visits on SWOT pass dates, labelling water masks, the thesis and the research paper.

## What we will deliver, and when (slide 19)

| When | What |
|---|---|
| Nov 2026 | Proposal, ethics and data requests |
| 15 Dec 2026 | Study area confirmed after the cascade and name checks |
| Dec 2026 – Apr 2027 | Labelled data, gauge readings, AI water model and SWOT curves |
| Mar – May 2027 | Storage estimates, validation and dashboard |
| 30 Jun 2027 | Thesis, paper and final submission |

## Datasets and links (slide 20)

Every dataset is free and public. Each link was opened and checked on 28 October 2026.

**Water height (SWOT)**

- [SWOT Lake and River Explorer](https://mibrechb.github.io/swot-data-explorer/): click any tank to see its readings
- [NASA Earthdata: SWOT lake product, version D](https://search.earthdata.nasa.gov/search/granules?p=C3233944983-POCLOUD): the files we use
- [Hydrocron](https://podaac.github.io/hydrocron/): the free service that gives each lake's heights

**Water area (pictures)**

- [Copernicus Browser](https://browser.dataspace.copernicus.eu/?themeId=DEFAULT-THEME&dateMode=SINGLE&zoom=14&lat=8.3868&lng=80.5471&datasetId=S2_L2A_CDAS&fromTime=2024-03-10T00%3A00%3A00.000Z&toTime=2024-03-10T23%3A59%3A59.999Z&layerId=1_TRUE_COLOR): Sentinel-1 and -2 pictures of our tanks
- [Planetary Computer: Sentinel-1 radar](https://planetarycomputer.microsoft.com/dataset/sentinel-1-rtc): terrain-corrected radar
- [ASF: NISAR radar](https://asf.alaska.edu/nisar/): L-band radar
- [JAXA ALOS-2 radar on AWS](https://registry.opendata.aws/jaxa-alos-palsar2-scansar/): L-band radar
- [S1S2-Water](https://doi.org/10.5281/zenodo.8314175): AI training data, 65 areas in 29 countries

**Ground truth**

- [Irrigation Department: reservoir water level](https://docs.google.com/spreadsheets/d/e/2PACX-1vTcSGhi9RESl7CMCl1TQnrKe07Gx5Q696YiSB9jneIHqIP9lifpqSErgI3D5k9KtQXSdW5JpycIIr5e/pubhtml): the daily sheet
- [Irrigation Department: reservoir status](https://irrigation.gov.lk/web/index.php?option=com_content&view=article&id=84&Itemid=201&lang=en): web page
- [Irrigation Department: reservoir map layer](https://services3.arcgis.com/J7ZFXmR8rSmQ3FGf/ArcGIS/rest/services/Scheme_Data_2/FeatureServer/10): full supply levels
- [Kanhindawewa drone survey](https://www.irrigation.gov.lk/web/images/Scheme-Maps/Anuradhapura/HuruluWewa/Area_Capacity_Kanhindawewa_01_07_2026.pdf): area and capacity every 1 ft (PDF)
- [Mahaweli Authority: reservoir status reports](https://mahaweli.gov.lk/wms.html): daily levels

**Weather (for the forecast)**

- [CHIRPS](https://www.chc.ucsb.edu/data/chirps): daily rainfall
- [ERA5](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels): weather, for evaporation
