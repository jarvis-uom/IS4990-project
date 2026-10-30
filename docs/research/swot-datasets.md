# Datasets: sizes, checks and who uses them (30 Oct 2026)

The same facts as the website's Datasets tab (https://swot.mehara.work/datasets.html). Sizes come from each provider's catalogue, read on 29 Oct 2026.

| Dataset | Members (main / checks) | Size we need | Verdict |
|---|---|---|---|
| SWOT lake product | B / A | Under 1 MB for our 13 tanks | Checked: works for us |
| SWOT pixel cloud | – / B | About 500 MB a file; about 100 files a tank | Stretch: not tested yet |
| ICESat-2 laser heights | – / B | Under 50 MB through SlideRule | For checks |
| Sentinel-2 photos | A / – | Small windows only | Works, with care: clouds and plants |
| Sentinel-1 radar | A / – | Small windows only; pieces about 14 MB | Works, with care: plants |
| L-band radar: NISAR and ALOS-2 | – / A | NISAR: about 4–5 GB a scene | New: not tested yet |
| OPERA water maps | – / A | 1–48 MB a map | For checks |
| Global Water Watch archive | B / – | 527 MB (one file) | Checked: works for us |
| JRC Global Surface Water | – / A | 18 MB (one tile) | For history and checks |
| AI training data: S1S2-Water and Sen1Floods11 | A / – | About 14 GB plus one 30 GB part | Works, with care: no water under plants |
| Irrigation Department daily storage | B, C / – | 13 MB | Checked: works, with care |
| Irrigation Department tank map (reservoir layer) | B / A | 6 MB | Checked: works, with care |
| Kanhindawewa drone survey | – / A, B | 2 MB (one PDF) | Checked: our best truth |
| Mahaweli reservoir status reports | – / B | A small PDF a day | For checks |
| Our gauge photos | B / A, C | A few MB a visit | To collect |
| Elevation map: Copernicus DEM (GLO-30) | B / A | 47 MB (one tile) | Works, with care: no tank beds |
| 3D-LAKES | – / B | 3 GB (all files) | For checks: big reservoirs only |
| Rain: GPM IMERG and CHIRPS | C / – | Small: our area, through Earth Engine | Works |
| ERA5 weather | C / – | 9 MB | Checked: works for us |

## Water height

How high the water stands. Member B turns it into how full each tank is.

### SWOT lake product

- **Provider:** NASA and CNES · version D · July 2023 onwards
- **Verdict:** Checked: works for us
- **What it gives:** A water height (and area) for every lake on each pass. SWOT sees all 13 study tanks about twice every 21 days.
- **Size:** One pass file for every lake: about 12 MB. Through Hydrocron a lake's whole record is tiny: all 677 lakes we checked came to 9 MB.
- **Is it right for us?**
    - All 13 study tanks have a SWOT lake ID, with 47–90 usable readings each since July 2023.
    - At the 5 big reservoirs SWOT reads 40–64 cm above the gauges: a steady gap, with only 7–13 cm of scatter.
    - Village tanks get almost only "suspect" readings, so Member B's trust screen cleans them first.
    - Official accuracy: 10 cm is required on lakes over 1 km²; 25 cm is the goal for smaller lakes.
- **How others used it:**
    - Das and Hossain, 2025: 245 reservoirs in 5 countries; SWOT height R² 0.91 (usual miss 92 cm) (https://doi.org/10.1029/2024EA004178)
    - Ma et al., 2026: 12 reservoirs in the western USA; height within 20 cm, storage within 10% (https://doi.org/10.1029/2025WR041223)
    - Li et al., 2026: 14 reservoirs; storage error 15% of capacity, 3% once tied to each reservoir's records (https://doi.org/10.3390/w18192462)
- **Ready-made tools:**
    - SWOT Lake and River Explorer (click any tank) (https://mibrechb.github.io/swot-data-explorer/)
    - Hydrocron (https://podaac.github.io/hydrocron/)
    - Our SWOT data page (https://swot.mehara.work/data.html)
- **Open the data:** NASA Earthdata: the files we use (https://search.earthdata.nasa.gov/search/granules?p=C3233944983-POCLOUD)
- **Used by:** Member A (checks or stretch), Member B (main)

### SWOT pixel cloud

- **Provider:** NASA and CNES · version D
- **Verdict:** Stretch: not tested yet
- **What it gives:** A height for every water pixel, including the shoreline. It also covers tanks that have no SWOT lake ID.
- **Size:** About 460–600 MB per file. About 100 files cover each of our tanks since July 2023.
- **Is it right for us?**
    - Only 58% of mapped tanks of 6.25 ha or more have a lake ID; the pixel cloud is how to add the rest.
    - Big files and an Earthdata login, so it stays a stretch goal.
- **How others used it:**
    - Köhn and Nielsen, 2026: 37 lakes in Denmark (25 ha to 40 km²); pixel-cloud water levels within 5–6 cm (https://doi.org/10.5194/hess-30-6443-2026)
- **Open the data:** NASA Earthdata search (https://search.earthdata.nasa.gov/search?q=SWOT_L2_HR_PIXC_D)
- **Used by:** Member B (checks or stretch)

### ICESat-2 laser heights

- **Provider:** NASA · ATL13 inland water · 2018 onwards
- **Verdict:** For checks
- **What it gives:** Water heights along narrow laser tracks. Each track repeats only every 91 days.
- **Size:** About 90–100 MB per file for a whole track. Through SlideRule we took only the points over our tanks: under 50 MB in all.
- **Is it right for us?**
    - Its beams crossed 12 of our 13 tanks: 12–23 dates at each big reservoir, but 0–5 at the village tanks.
    - Against SWOT, 13 of 14 pairs taken within 4 days agree within 15 cm.
- **How others used it:**
    - Madumalsha et al., 2025: 9 Sri Lankan reservoirs; correlation 0.99 with the gauges, but 37 cm too high on average (https://doi.org/10.4038/engineer.v58i1.7674)
- **Ready-made tools:**
    - SlideRule (no login) (https://slideruleearth.io)
- **Open the data:** NASA Earthdata search (https://search.earthdata.nasa.gov/search?q=ATL13)
- **Used by:** Member B (checks or stretch)

## Water area: pictures from space

Where the water is. Member A's water map learns from these pictures.

### Sentinel-2 photos

- **Provider:** Copernicus (ESA) · 10 m · 2015 onwards
- **Verdict:** Works, with care: clouds and plants
- **What it gives:** Colour and infrared photos at 10 m. Our tanks get about 89 pictures a year (one tile, 44PMQ).
- **Size:** 230–640 MB per scene (a 110 km square). We read only small windows around each tank: our check of over 400 scenes read about 200 MB.
- **Is it right for us?**
    - Only 8–12% of scenes are fully clear over Mahakanadarawa. The best months are March and September–October.
    - At plant-covered Kanhindawewa, a simple water index (NDWI) missed about 65% of the water.
    - At 10 m a 6 ha tank is 600 pixels, against 67 at 30 m, so it suits small tanks.
- **How others used it:**
    - IFAD and ESA, 2026: monthly 10 m water maps of over 10,650 water bodies in 6 Sri Lankan districts, 2017 to August 2025 (https://www.ifad.org/en/w/publications/water-surface-maps-to-manage-ancient-tank-cascade-systems-in-sri-lanka)
    - Dossou Codjia et al., 2025: 20 reservoirs in Burkina Faso; R² 0.76–0.97 at 14, but plants hid the water at 6 (https://doi.org/10.1016/j.jag.2025.104523)
    - Pascal et al., 2024: 504 tanks in Telangana, India; a 17% area error became a 31% volume error (https://doi.org/10.1371/journal.pwat.0000260)
- **Ready-made tools:**
    - Copernicus Browser (opens on Mahakanadarawa) (https://browser.dataspace.copernicus.eu/?themeId=DEFAULT-THEME&dateMode=SINGLE&zoom=14&lat=8.3868&lng=80.5471&datasetId=S2_L2A_CDAS&fromTime=2024-03-10T00%3A00%3A00.000Z&toTime=2024-03-10T23%3A59%3A59.999Z&layerId=1_TRUE_COLOR)
    - Dynamic World water class (https://developers.google.com/earth-engine/datasets/catalog/GOOGLE_DYNAMICWORLD_V1)
- **Open the data:** Sentinel-2 in Google Earth Engine (surface reflectance, from 2017) (https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED)
- **Used by:** Member A (main)

### Sentinel-1 radar

- **Provider:** Copernicus (ESA) · C-band · 2014 onwards
- **Verdict:** Works, with care: plants
- **What it gives:** Radar pictures that see through cloud, day and night. Our tanks get one radar date every 12 days: tracks 19 and 27 pass on the same day, morning and evening. Since June 2026 Sentinel-1D takes these pictures; the new 6-day repeat has not reached our area.
- **Size:** About 1–2 GB per scene. Ready-made terrain-corrected pieces (OPERA RTC-S1) are about 14 MB each.
- **Is it right for us?**
    - It sees the water through monsoon cloud, when photos see nothing.
    - Thick floating plants look like land to it: at Kanhindawewa a simple −18 dB rule found only about a tenth of the water.
- **How others used it:**
    - Perera and Jayaweera, 2020: Sri Lankan reservoirs; radar water area against reported volume, R² 0.67–0.94 (https://archive.cmb.ac.lk/items/84f64851-eaa9-4b8c-babd-5d18f130c1ee)
    - Wieland et al., 2024: a U-Net on radar matched 85% of the true water (https://doi.org/10.1109/JSTARS.2023.3333969)
- **Ready-made tools:**
    - Planetary Computer: terrain-corrected Sentinel-1 (https://planetarycomputer.microsoft.com/dataset/sentinel-1-rtc)
- **Open the data:** Sentinel-1 in Google Earth Engine (https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S1_GRD)
- **Used by:** Member A (main)

### L-band radar: NISAR and ALOS-2

- **Provider:** NASA–ISRO (NISAR, 2025 onwards) · JAXA (ALOS-2, 2014 onwards)
- **Verdict:** New: not tested yet
- **What it gives:** Longer-wave radar that sees further into plants. NISAR gives about 5 pictures a month here; free ALOS-2 pictures come about 10 times a year.
- **Size:** NISAR: about 4–5 GB per scene for the map-ready version (GCOV); the raw versions are 15–26 GB. ALOS-2: size not checked.
- **Is it right for us?**
    - NISAR already has pictures over our tanks (October 2026). Its public release covers passes from 17 June 2026; older ones are being released.
    - It should see water under floating plants better than Sentinel-1. We have not tested it on our tanks yet.
    - The free ALOS-2 copy on AWS covers Africa only, so ours would come from Earth Engine.
- **How others used it:**
    - NISAR's data only became public in July 2026, so we found no tank study yet.
- **Ready-made tools:**
    - ALOS-2 ScanSAR in Google Earth Engine (25 m) (https://developers.google.com/earth-engine/datasets/catalog/JAXA_ALOS_PALSAR-2_Level2_2_ScanSAR)
- **Open the data:** ASF: NISAR data (https://asf.alaska.edu/nisar/)
- **Used by:** Member A (checks or stretch)

### OPERA water maps

- **Provider:** NASA · DSWx · 30 m
- **Verdict:** For checks
- **What it gives:** Ready-made water maps: one from each photo (DSWx-HLS, validated maps since April 2023) and one from each radar picture (DSWx-S1, since August 2024).
- **Size:** About 48 MB per photo-based map and 1–10 MB per radar-based map, for one tile.
- **Is it right for us?**
    - Over our tile: 109 photo-based maps and 26 radar dates in 12 months.
    - 30 m pixels are coarse for small tanks. The radar version has an "inundated vegetation" (water under plants) class, but only for water bodies over 3 ha and 200 m wide. A ready-made baseline for Member A's maps.
- **Open the data:** NASA Earthdata search (https://search.earthdata.nasa.gov/search?q=OPERA_L3_DSWX-S1_V1)
- **Used by:** Member A (checks or stretch)

### Global Water Watch archive

- **Provider:** Global Water Watch · Landsat and Sentinel-2 · saved September 2026
- **Verdict:** Checked: works for us
- **What it gives:** Water area over time for 71,208 reservoirs worldwide. The archive was saved before the service closes.
- **Size:** One 527 MB file for every reservoir. Hurulu Wewa's record since October 2020 is 147 areas.
- **Is it right for us?**
    - We matched 69 of the department's 117 reservoirs by their outlines (78% overlap on the median), giving 11,484 area–storage pairs to train Member B's model.
    - Cloud gaps are filled in by its method, not measured. It has no village tanks.
- **How others used it:**
    - Donchyts et al., 2022: the method behind it, for small and medium reservoirs worldwide (https://doi.org/10.1038/s41598-022-17074-6)
- **Ready-made tools:**
    - Global Water Watch website (offline from November 2026) (https://www.globalwaterwatch.earth/)
- **Open the data:** Zenodo: the archive (CC BY 4.0) (https://zenodo.org/records/22643338)
- **Used by:** Member B (main)

### JRC Global Surface Water

- **Provider:** European Commission JRC · Landsat · 1984 onwards
- **Verdict:** For history and checks
- **What it gives:** Monthly 30 m water maps since 1984, and how often each pixel was wet.
- **Size:** One 10° × 10° tile of "how often wet": 18 MB.
- **Is it right for us?**
    - Its newest month is December 2024, so it gives history, not new dates.
    - Each tank was fully seen in 21–22 of the 36 months of 2022–24. Its "how often wet" map can give each tank's largest outline.
- **How others used it:**
    - Pekel et al., 2016 (Nature): the dataset paper (https://doi.org/10.1038/nature20584)
- **Open the data:** JRC Global Surface Water downloads (https://global-surface-water.appspot.com/download)
- **Used by:** Member A (checks or stretch)

## AI training data

Pictures where people have already drawn the water in. Member A's AI learns from them what water looks like.

### AI training data: S1S2-Water and Sen1Floods11

- **Provider:** DLR (S1S2-Water) · Cloud to Street (Sen1Floods11)
- **Verdict:** Works, with care: no water under plants
- **What it gives:** Hand-checked water masks for Sentinel-1 and Sentinel-2 pictures. S1S2-Water covers 65 areas in 29 countries; Sen1Floods11 covers flood events.
- **Size:** S1S2-Water (v1.0.1): 166 GB in 6 parts of 20–33 GB, plus a catalogue file. Sen1Floods11: about 14 GB. We plan Sen1Floods11 plus one part of S1S2-Water.
- **Is it right for us?**
    - U-Nets trained on S1S2-Water matched 97% of the true water on photos and 85% on radar.
    - Neither has a "water under plants" class, so we add our own labels from our tanks.
- **How others used it:**
    - Wieland et al., 2024: the S1S2-Water paper (https://doi.org/10.1109/JSTARS.2023.3333969)
    - Bonafilia et al., 2020: the Sen1Floods11 paper (CVPR workshops)
- **Ready-made tools:**
    - Sen1Floods11 on GitHub (https://github.com/cloudtostreet/Sen1Floods11)
- **Open the data:** Zenodo: S1S2-Water v1.0.1 (https://doi.org/10.5281/zenodo.11278238)
- **Used by:** Member A (main)

## Ground truth

Measured on the ground: what we train on and test against.

### Irrigation Department daily storage

- **Provider:** Irrigation Department of Sri Lanka · Reservoir Status · 2020 onwards
- **Verdict:** Checked: works, with care
- **What it gives:** Daily storage of 117 reservoirs (74 major since October 2020, 43 medium since April 2023), with capacity, and daily gauge depth for the big ones.
- **Size:** About 200,000 daily values: a 13 MB table.
- **Is it right for us?**
    - The department's own public dashboards read this same sheet.
    - The Reservoir Status page shows only the latest day, but four tabs of the same sheet keep every day: since October 2020 for the major reservoirs, and since 2023 for the medium ones. The download links are below.
    - Our logger saves every tab of it three times a day, and the department's report as PDF once a week, so nothing is lost if the sheet changes.
    - The value changes on only 34–62% of days at the big reservoirs, so some days are not updated.
    - Its "long-term average" column is the average of the seasons in the sheet, including the latest years. It must not be used to test forecasts.
    - On 27 October 2026 it differed from the Mahaweli Authority's figure for Nachchaduwa by 4%.
- **How others used it:**
    - It trains Member B's storage model and Member C's forecast, and labels the trust screen.
- **Ready-made tools:**
    - Reservoir Status page (https://irrigation.gov.lk/web/index.php?option=com_content&view=article&id=84&Itemid=201&lang=en)
    - The department's map: Major Reservoirs Water Level (ArcGIS) (https://www.arcgis.com/home/item.html?id=9b5ee8a0b2744f0d838c12d0d3b47547)
- **Download the daily history (CSV):**
    - Major reservoirs, Maha seasons, 2020/21 onwards (https://docs.google.com/spreadsheets/d/e/2PACX-1vTcSGhi9RESl7CMCl1TQnrKe07Gx5Q696YiSB9jneIHqIP9lifpqSErgI3D5k9KtQXSdW5JpycIIr5e/pub?gid=673998835&single=true&output=csv)
    - Major reservoirs, Yala seasons, 2022 onwards (https://docs.google.com/spreadsheets/d/e/2PACX-1vTcSGhi9RESl7CMCl1TQnrKe07Gx5Q696YiSB9jneIHqIP9lifpqSErgI3D5k9KtQXSdW5JpycIIr5e/pub?gid=1244158041&single=true&output=csv)
    - Medium reservoirs, Maha seasons, 2024/25 onwards (https://docs.google.com/spreadsheets/d/e/2PACX-1vTcSGhi9RESl7CMCl1TQnrKe07Gx5Q696YiSB9jneIHqIP9lifpqSErgI3D5k9KtQXSdW5JpycIIr5e/pub?gid=155979206&single=true&output=csv)
    - Medium reservoirs, Yala seasons, 2023 onwards (https://docs.google.com/spreadsheets/d/e/2PACX-1vTcSGhi9RESl7CMCl1TQnrKe07Gx5Q696YiSB9jneIHqIP9lifpqSErgI3D5k9KtQXSdW5JpycIIr5e/pub?gid=1831537855&single=true&output=csv)
- **Open the data:** The daily sheet (https://docs.google.com/spreadsheets/d/e/2PACX-1vTcSGhi9RESl7CMCl1TQnrKe07Gx5Q696YiSB9jneIHqIP9lifpqSErgI3D5k9KtQXSdW5JpycIIr5e/pubhtml)
- **Used by:** Member B (main), Member C (main)

### Irrigation Department tank map (reservoir layer)

- **Provider:** Irrigation Department of Sri Lanka · "as at 1 January 2022"
- **Verdict:** Checked: works, with care
- **What it gives:** A map layer of 354 irrigation schemes: full-supply outline and area, capacity, dead storage, catchment, flood level and bund top.
- **Size:** 354 outlines: a 6 MB file.
- **Is it right for us?**
    - 258 tanks have both capacity and area (81 major, 164 medium, 13 minor). 116 of the 117 daily-sheet reservoirs sit on an outline.
    - It gives no survey year. Mahakanadarawa's spill was raised in 2024–26, so its capacity rose from 45 to 47 million m³, but the layer still shows the old level.
    - None of our 8 village tanks is in it (checked 30 October 2026), so their outlines come from OpenStreetMap.
- **Ready-made tools:**
    - Scheme Register 2022 (PDF) (https://irrigation.gov.lk/web/images/Publications/SCHEME_REGISTER_2ND_EDITION_Book__2022.pdf)
- **Open the data:** The map layer (ArcGIS) (https://services3.arcgis.com/J7ZFXmR8rSmQ3FGf/ArcGIS/rest/services/Scheme_Data_2/FeatureServer/10)
- **Used by:** Member A (checks or stretch), Member B (main)

### Kanhindawewa drone survey

- **Provider:** Irrigation Department · LiDAR drone and GNSS · 2026
- **Verdict:** Checked: our best truth
- **What it gives:** A measured tank bed: the area and capacity of Kanhindawewa at every foot of height.
- **Size:** One 2 MB PDF.
- **Is it right for us?**
    - The only measured tank bed we have: full supply at 260 ft, 83.5 ha and 817 acre-feet.
    - On it, Imbulana's formula gave 4–14% too much water above one-third depth (our test).
    - We show no picture of it: reusing the map needs the Director General of Irrigation's approval.
- **Ready-made tools:**
    - Our Drone survey page (https://swot.mehara.work/drone.html)
- **Open the data:** The survey sheet (PDF) (https://www.irrigation.gov.lk/web/images/Scheme-Maps/Anuradhapura/HuruluWewa/Area_Capacity_Kanhindawewa_01_07_2026.pdf)
- **Used by:** Member A (checks or stretch), Member B (checks or stretch)

### Mahaweli reservoir status reports

- **Provider:** Mahaweli Authority · Water Management Secretariat
- **Verdict:** For checks
- **What it gives:** Water level in metres above sea level, and storage, for Hurulu Wewa, Nachchaduwa and Nuwara Wewa.
- **Size:** A small PDF each day. Only today's is online: it is replaced daily.
- **Is it right for us?**
    - Its sea-level readings matched our "gauge zero" sum (full supply level minus full depth) within 11 cm on 27 October 2026.
    - It must be saved every day, or the record is lost. Our logger keeps every new one, with the Secretariat's other PDFs (from 29 October 2026, plus a copy from 27 October).
- **Open the data:** Reservoirs status reports (https://mahaweli.gov.lk/wms.html)
- **Used by:** Member B (checks or stretch)

### Our gauge photos

- **Provider:** Collected by the team · on SWOT pass days
- **Verdict:** To collect
- **What it gives:** Photos of the gauge posts at the village tanks, with time and GPS, on the days SWOT passes.
- **Size:** A few MB of phone photos a visit.
- **Is it right for us?**
    - The only height check at village tanks that have no records.
    - Visits are in daylight and in pairs, and nobody enters the water.
- **Ready-made tools:**
    - Our Calendar page: the pass days (https://swot.mehara.work/calendar.html)
- **Used by:** Member A (checks or stretch), Member B (main), Member C (checks or stretch)

## Ground and tank-bed shape

The land around each tank, and the shape of the bed.

### Elevation map: Copernicus DEM (GLO-30)

- **Provider:** Copernicus · 30 m · radar from 2011–12 here
- **Verdict:** Works, with care: no tank beds
- **What it gives:** Ground height every 30 m. Member B takes land slope and catchment from it; Member A uses the slope.
- **Size:** One 1° × 1° tile is 47 MB, and one tile covers all 13 of our tanks.
- **Is it right for us?**
    - Water is flattened: 70–95% of each big reservoir is one flat value, so the bed is missing.
    - On dry beds it is within about 1 m of ICESat-2: the best of the free elevation maps here.
- **How others used it:**
    - Pascal et al., 2024: global elevation maps gave 47–78% volume errors on small reservoirs (https://doi.org/10.1371/journal.pwat.0000260)
    - Das and Hossain, 2025: curves from SRTM elevation can be off by a few metres (https://doi.org/10.1029/2024EA004178)
- **Open the data:** Copernicus DEM on AWS (https://registry.opendata.aws/copernicus-dem/)
- **Used by:** Member A (checks or stretch), Member B (main)

### 3D-LAKES

- **Provider:** Huang et al. · ICESat-2 and Landsat · 2025
- **Verdict:** For checks: big reservoirs only
- **What it gives:** Height–area–volume curves for lakes and reservoirs worldwide.
- **Size:** 3 GB in 8 files.
- **Is it right for us?**
    - Curves are about 60 cm off (median) against 214 surveyed curves.
    - It covers 510,530 lakes, but most lakes under 1 km² have no curve. So it may only check the 5 big reservoirs; whether our village tanks have curves is still to check.
- **How others used it:**
    - Huang et al., 2025 (Scientific Data): the dataset paper (https://doi.org/10.1038/s41597-025-05911-y)
- **Open the data:** Zenodo: 3D-LAKES (https://zenodo.org/records/13107867)
- **Used by:** Member B (checks or stretch)

## Weather

Rain and evaporation, for Member C's forecast.

### Rain: GPM IMERG and CHIRPS

- **Provider:** NASA (IMERG, 2000 onwards) · UC Santa Barbara (CHIRPS, 1981 onwards)
- **Verdict:** Works
- **What it gives:** Daily rain from satellites. As in the proposal, IMERG (10 km, only one day behind) is the daily input, and CHIRPS (5 km, corrected with rain gauges) is for monthly checks.
- **Size:** IMERG: about 27 MB a day for the whole world. CHIRPS: about 3 MB a day.
- **Is it right for us?**
    - In Sri Lanka, IMERG is better day by day and CHIRPS month by month.
    - CHIRPS version 2 ends after December 2026, so we will use version 3 (already out, same grid).
    - Final CHIRPS data runs about a month behind, with an early version about a week behind.
    - We have not yet checked either against Sri Lankan rain gauges.
- **How others used it:**
    - Perera et al., 2026: IMERG better daily, CHIRPS better monthly, in Sri Lanka (https://doi.org/10.5194/egusphere-egu26-20641)
    - Funk et al., 2015 (Scientific Data): the CHIRPS paper (https://doi.org/10.1038/sdata.2015.66)
- **Ready-made tools:**
    - GPM IMERG (NASA) (https://gpm.nasa.gov/data/imerg)
- **Open the data:** CHIRPS (https://www.chc.ucsb.edu/data/chirps)
- **Used by:** Member C (main)

### ERA5 weather

- **Provider:** Copernicus Climate Change Service · 25 km · 1940 onwards
- **Verdict:** Checked: works for us
- **What it gives:** Hourly weather on a 25 km grid: rain, temperature, wind and evaporation. Open-Meteo serves it free, with no key.
- **Size:** Our daily rain for 117 reservoirs, 2020–2026: a 9 MB table.
- **Is it right for us?**
    - In our forecast test, past rain helped a little; knowing the coming weeks' rain cut the error by another 6–9%.
    - It runs about 6 days behind.
- **How others used it:**
    - Hersbach et al., 2020: the ERA5 paper (https://doi.org/10.1002/qj.3803)
- **Ready-made tools:**
    - Open-Meteo archive API (https://open-meteo.com/en/docs/historical-weather-api)
- **Open the data:** ERA5 at the Climate Data Store (https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels)
- **Used by:** Member C (main)
