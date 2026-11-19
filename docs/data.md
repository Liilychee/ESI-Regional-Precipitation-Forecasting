# Data access and attribution

- [ERA5 hourly data on single levels](https://doi.org/10.24381/cds.adbb2d47) supplies the main record and the 1992–2003 rolling-origin extension. Use the reanalysis product and the Dublin domain 52.75–53.75°N, 6.75–5.75°W. Follow the CDS product licence and citation requirements.
- [ERA5 hourly data on pressure levels](https://doi.org/10.24381/cds.bd0915c6) supplies upstream 500 hPa geopotential. The upstream domain and configuration vary by diagnostic. See the feature-building script and manuscript methods.
- [WeatherBench 2 data guide](https://weatherbench2.readthedocs.io/en/latest/data-guide.html) describes the ECMWF IFS HRES and ERA5 archives. Check the licence for the exact source assets. The comparison uses 00/12 UTC initializations and common 06/18 UTC valid times. Regional NetCDF extracts are external inputs under `data/q08/HRES/` and `data/q08/WeatherBench/`.
- [Met Éireann Dublin Airport hourly data, station 532](https://clidata.met.ie/cli/climate_data/webdata/hly532.csv) is the station source used by the exploratory comparison. Save it locally as `data/hly532.csv`. Follow the [dataset attribution and licence guidance](https://www.met.ie/about-us/specialised-services/open-data).

The primary input fields comprise `tp` plus `u10`, `v10`, `d2m`, `t2m`, `sp`, `e`, `mxtpr`, `mntpr`, `tcc`, `ssr`, and `lsp`. Retain the native variable units and UTC valid times. Average the 25 grid points with equal weights. Sample 00, 06, 12, and 18 UTC and multiply `tp` by 1,000 to obtain millimetres. The target is the single-hour accumulation ending at the valid time. The regional input expected by the baseline scripts is `data/dublin_regional_reduced.csv`. The original grid-level CSV expected by several scripts is `data/04-24.csv`. A complete verified retrieval and conversion recipe for that historical input is pending.

## Licence and attribution scope

The [BSD-3-Clause licence](../LICENSE) covers the Python source code. Data and scientific result files are outside its scope. This repository includes selected summary results. Raw meteorological data, full forecast CSVs, HRES and station results, and the complete ECDF are withheld. The HRES and station links are provided for independent access.

The results contain modified Copernicus Climate Change Service information (1992–2021). Neither the European Commission nor ECMWF is responsible for any use that may be made of the Copernicus information or data it contains.

The original CDS ERA5 products are available under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/). Cite the catalogue entries for [ERA5 hourly data on single levels](https://doi.org/10.24381/cds.adbb2d47) and, for the upstream experiment, [ERA5 hourly data on pressure levels](https://doi.org/10.24381/cds.bd0915c6). The retained results reflect spatial aggregation, UTC sampling, precipitation unit conversion, and subsequent analysis as applicable. For raw data access, use the relevant CDS catalogue page, sign in, accept its terms, and use the Download form or corresponding API request. The exact historical conversion is subject to the input limitations described above.

| Source | Asset and attribution to record |
|---|---|
| CDS ERA5 single and pressure levels | Cite both relevant catalogue DOIs and record source dates, Copernicus/C3S credit, modified information and applicable notices. Explain regional aggregation, sampling and metre-to-millimetre conversion. See the [ECMWF ERA5 attribution example](https://confluence.ecmwf.int/spaces/CKB/pages/222493847/Use%2BCase%2B2%2BERA5%2Bhourly%2Bdata%2Bon%2Bsingle%2Blevels%2Bfrom%2B1940%2Bto%2Bpresent). |
| WeatherBench 2 HRES | The historical source is `datasets/hres/2016-2022-0012-1440x721.zarr`. The [official HRES notice](https://storage.googleapis.com/storage/v1/b/weatherbench2/o/datasets%2Fhres%2FLICENSE?alt=media) specifies CC BY 4.0, ECMWF credit, licence, disclaimer and modification statement. |
| WeatherBench 2 ERA5 | The comparison used `datasets/era5/1959-2022-6h-1440x721.zarr` and `datasets/era5/1959-2022-full_37-1h-0p25deg-chunk-1.zarr-v2`. The [official dataset notice](https://storage.googleapis.com/storage/v1/b/weatherbench2/o/datasets%2Fera5%2FLICENSE?alt=media) provides separate Copernicus terms. |
| Met Éireann Dublin Airport 532 | The [official station resource](https://data.gov.ie/en_GB/dataset/dublin-airport-hourly-data/resource/a818dbd2-c82a-4514-8ff3-62a63c0b9ba3) specifies CC BY 4.0. Record the downloaded version and the applicable copyright, source, licence, disclaimer and modification notice. |

For the rolling-origin workflow, supply the annual 1992–2003 extracts as `data/era5_1992_2003/era5_*.nc`, plus the main-period grid CSV and reference regional CSV. [The regional builder](../code/q06_build_regional.py) writes `data/q06/dublin_regional_1992_2021.csv`. Upstream and hourly workflows additionally require matched hourly or pressure-level files and their experiment-specific regional inputs. See the [figure and table index](figure_table_map.tsv) for paths and unavailable snapshots.

The study-area image from the manuscript is omitted. A separate schematic can show the geographic extent and 25 grid-point centres using a separately licensed or self-drawn map.
