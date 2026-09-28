# pm-pv-pathway

Data and code for "Particulate Matter Pollution and Utility-Scale Photovoltaic Output: Evidence for the Pollution–Irradiance–Output Pathway from Solar Farms in China"

## Repository contents

| Path | Description |
|---|---|
| `PV_Yulin/` | PV operating records for the five utility-scale farms in Yulin, China (2021), 15-minute resolution |
| `Installed Capacity.txt` | Installed capacity of the Hebei (10 farms) and Yulin (5 farms) plants |

## Data sources

| Dataset | Source | Available here |
|---|---|---|
| Yulin PV operating data (5 farms, 2021) | Farm operating records used in this study | Yes — `PV_Yulin/` |
| Hebei PV operating data (10 farms, 2018–2019) | PVOD, Yao et al. (2021), *Solar Energy* — https://github.com/yaotc/PVODataset | No — obtain from the original repository |
| Hourly PM2.5 and PM10 | http://eia-data.com/pm25_hour/ | No — too large to host |
| Historical weather variables | https://open-meteo.com/ | No — too large to host |

**The Hebei PV data are the public PVOD dataset and are not redistributed in this repository.** Please obtain them directly from https://github.com/yaotc/PVODataset and cite the original publication.

The air-quality and weather datasets are publicly downloadable from the sources listed above but are too large to include here. The analysis matches them to each farm by location and timestamp; see the manuscript for the matching procedure.

## File format — `PV_Yulin/`

One `.xlsx` file per farm, 15-minute resolution, covering 2021-01-01 to 2021-12-31.

| Column | Meaning | Unit |
|---|---|---|
| `time` | Timestamp, local time (Beijing) | — |
| `ghi` | Global horizontal irradiance | W m⁻² |
| `direct` | Direct horizontal component | W m⁻² |
| `diffuse` | Diffuse irradiance | W m⁻² |
| `temperature` | Air temperature | °C |
| `pressure` | Surface pressure | hPa |
| `humidity` | Relative humidity | % |
| `power_mw` | Actual power output | MW |
| `capacity_mw` | Installed capacity | MW |

Notes for reuse:

- Each file contains 35,025–35,026 data rows against 35,040 expected 15-minute intervals in 2021 (≈99.96% complete).
- `direct` is a horizontal-plane direct component. It is close to, but not exactly, `ghi − diffuse` (1–5% higher). The analyses in the paper define the direct component as `ghi − diffuse` truncated at zero, so that the definition is identical in both regions — the Hebei source does not report a direct column.
- The raw 15-minute records are aggregated to hourly resolution before matching with the air-quality and weather data.

## Installed capacity

`Installed Capacity.txt` lists the capacity of each plant in order:

- Hebei: 6.6, 20, 17, 20, 20, 35, 15, 20, 20, 20 MW — corresponding to `station00`–`station09`
- Yulin: 30, 50, 20, 20, 200 MW — corresponding to `Site1`–`Site5`

## Code

Analysis code will be made available upon acceptance of the manuscript.
