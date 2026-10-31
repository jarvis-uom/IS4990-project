# Presentation

The proposal talk: 15 slides, submitted with the proposal on 30 October 2026.

| File | What it is |
|---|---|
| [swot-tank-tracker-proposal-talk.pdf](swot-tank-tracker-proposal-talk.pdf) | The slides as a PDF (3.4 MB) |
| [swot-tank-tracker-proposal-talk.pptx](swot-tank-tracker-proposal-talk.pptx) | The PowerPoint, if you want to edit it (6.9 MB) |

You can also flip through the slides on the website: <https://swot.mehara.work/presentation>. The speaker notes are kept private, so these copies have none, and our names are left out: the modules' owners are shown as Member A, B and C.

## Who does what: one model each (slides 5 to 14)

Our three models form one chain: A finds where the water is (a U-Net water map), B works out how much water there is (a gradient-boosting model that turns SWOT height and water area into % full, after a trust screen cleans the SWOT readings), and C says what comes next (an LSTM storage forecast). Slide 5 gives the overview; slides 6 to 8 cover Module A, 9 to 11 Module B and 12 to 14 Module C. The same plan is on the website's Team tab: <https://swot.mehara.work/team>.

| Member | Research question | Data analysis | Technical work | Output |
|---|---|---|---|---|
| A: AI water maps | RQ1 | Label water masks with a "water under plants" class; score the maps (IoU, F1); area error against Kanhindawewa's drone survey; compare with the simple rules and SWOT's own area | **Model: a U-Net** (EfficientNet-B0) trained on S1S2-Water, then fine-tuned on our tanks; Sentinel-1, NISAR, Sentinel-2 and slope as inputs; a pipeline from picture day to water area | Water area for every tank on every picture day, with its accuracy |
| B: SWOT and storage | RQ2 and RQ3 | SWOT minus gauge on every pass (gap and spread in cm); the trust screen: how many "suspect" readings it keeps, and their error; training pairs of daily storage with SWOT height and water area at about 100 reservoirs; storage error in % of capacity on reservoirs the model never saw, against one formula for all tanks | Hydrocron pipeline; trust screen (gradient boosting) on SWOT's quality fields, track distance, lake size and season; **model: a storage model** (gradient boosting in which more height or area never means less water), using only inputs every tank has: height, area, outline, catchment and slope (Copernicus DEM) | SWOT accuracy report, a screen that cleans every reading, and a model that says how full any tank is |
| C: Forecast and system | RQ4 | Seasonal average for each tank, from past years only; forecast error at 2 and 4 weeks against "no change" and the seasonal average, on years and reservoirs the model never saw; the whole chain, picture to forecast, at the village tanks and on Kanhindawewa's drone survey | **Model: a storage forecast** (an LSTM with a gradient-boosting baseline, trained on the daily storage of 117 reservoirs (74 since 2020, 43 since 2023), with rain and evaporation); the chain after every pass (A's water map and SWOT's height into B's model); the dashboard; automatic updates with GitHub Actions | A 2–4 week forecast for every tank, the running chain and the dashboard |

All three of us: field visits on SWOT pass dates, labelling water masks, the thesis and the research paper.

## What we will deliver, and when (slide 15)

| When | What |
|---|---|
| Nov 2026 | Proposal, ethics and data requests |
| 15 Dec 2026 | Study area confirmed after the cascade and name checks |
| Dec 2026 – Apr 2027 | Labelled data, gauge readings, and the three models: water map, storage model, forecast |
| Mar – May 2027 | Storage estimates, validation and dashboard |
| 30 Jun 2027 | Thesis, paper and final submission |

## Datasets and links

Every dataset is free and public. Each link was opened and checked on 28 October 2026 (the three added on 29 October too).

**Water height (SWOT)**

- [SWOT Lake and River Explorer](https://mibrechb.github.io/swot-data-explorer/): click any tank to see its readings
- [NASA Earthdata: SWOT lake product, version D](https://search.earthdata.nasa.gov/search/granules?p=C3233944983-POCLOUD): the files we use
- [Hydrocron](https://podaac.github.io/hydrocron/): the free service that gives each lake's heights

**Water area (pictures)**

- [Copernicus Browser](https://browser.dataspace.copernicus.eu/?themeId=DEFAULT-THEME&dateMode=SINGLE&zoom=14&lat=8.3868&lng=80.5471&datasetId=S2_L2A_CDAS&fromTime=2024-03-10T00%3A00%3A00.000Z&toTime=2024-03-10T23%3A59%3A59.999Z&layerId=1_TRUE_COLOR): Sentinel-1 and -2 pictures of our tanks
- [Planetary Computer: Sentinel-1 radar](https://planetarycomputer.microsoft.com/dataset/sentinel-1-rtc): terrain-corrected radar
- [ASF: NISAR radar](https://asf.alaska.edu/nisar/): L-band radar
- [JAXA ALOS-2 radar on AWS](https://registry.opendata.aws/jaxa-alos-palsar2-scansar/): L-band radar
- [S1S2-Water](https://doi.org/10.5281/zenodo.11278238): AI training data, 65 areas in 29 countries
- [Global Water Watch archive](https://zenodo.org/records/22643338): reservoir water areas

**Ground shape**

- [Copernicus DEM (GLO-30)](https://registry.opendata.aws/copernicus-dem/): 30 m elevation map

**Ground truth**

- [Irrigation Department: reservoir water level](https://docs.google.com/spreadsheets/d/e/2PACX-1vTcSGhi9RESl7CMCl1TQnrKe07Gx5Q696YiSB9jneIHqIP9lifpqSErgI3D5k9KtQXSdW5JpycIIr5e/pubhtml): the daily sheet
- [Irrigation Department: reservoir status](https://irrigation.gov.lk/web/index.php?option=com_content&view=article&id=84&Itemid=201&lang=en): web page
- [Irrigation Department: reservoir map layer](https://services3.arcgis.com/J7ZFXmR8rSmQ3FGf/ArcGIS/rest/services/Scheme_Data_2/FeatureServer/10): full supply levels
- [Kanhindawewa drone survey](https://www.irrigation.gov.lk/web/images/Scheme-Maps/Anuradhapura/HuruluWewa/Area_Capacity_Kanhindawewa_01_07_2026.pdf): area and capacity every 1 ft (PDF)
- [Mahaweli Authority: reservoir status reports](https://mahaweli.gov.lk/wms.html): daily levels

**Weather (for the forecast)**

- [GPM IMERG](https://gpm.nasa.gov/data/imerg): daily rainfall
- [CHIRPS](https://www.chc.ucsb.edu/data/chirps): monthly rainfall checks
- [ERA5](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels): weather, for evaporation
