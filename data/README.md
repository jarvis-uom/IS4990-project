# Data

Large files don't go in git. They live in the [shared Google Drive folder](https://drive.google.com/drive/folders/1xuW6Cw29zui5nStpL95cumJzVbLcgkLW) (team members only).

Only small samples, each under about 5 MB, go in this repo, in `data/samples/`. Git ignores everything else in this folder.

## Public datasets on Kaggle

Module A's satellite chips are public on Kaggle under CC BY 4.0, so anyone can reuse them. Each dataset is about 12 GB, and downloading needs a free Kaggle account.

| Dataset | What is in it |
|---|---|
| [Sri Lankan Reservoirs: Sentinel-1 and 2 Chips](https://www.kaggle.com/datasets/mehararothila/is4990-module-a-first-check-chips) | 3,843 chips of 117 reservoirs: Sentinel-1 radar, Sentinel-2 bands, JRC water occurrence and Cloud Score+, on clear and cloudy days from July 2023 to December 2025 |
| [Sri Lankan Reservoirs: Every Sentinel-1 Pass](https://www.kaggle.com/datasets/mehararothila/is4990-module-a-pass-chips) | 16,552 radar chips (VV and VH) of the same 117 reservoirs, one orbit each, from October 2020 to October 2026 |

Both datasets hold images and descriptions only. Module A's code is public in the [Module A write-up](https://github.com/jarvis-uom/Mehara/tree/main/swot-tank-tracker/module-a); the Irrigation Department's tables and the trained models stay private.
