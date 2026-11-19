# Short-Term Regional Precipitation Forecasting over Dublin Using ERA5 Reanalysis: Robustness, Probabilistic Reliability, and Predictor Attribution

Yue Li and Soumyabrata Dev

This repository accompanies a retrospective six-hour-ahead forecast study for Dublin. The target is the final-hour precipitation averaged over 25 ERA5 grid cells. The main record spans 2004–2021. The rolling-origin experiment extends the source record to 1992.

## Scope

- **Check from included results.** The six learning-model rows in Table 3 and the original Gaussian summaries in Table 5 A1 can be recomputed from the included seed-level metrics. Figure 5 fixed and validation-selected CSI can be checked from the archived event counts. Figures 2, 6–8 and the supplementary spatial-quantiles plot have the inputs needed for PGF redraws.
- **Archived summaries.** Table 4, Table 5 A2 and B, Figure 3 and selected supplementary analyses have saved summary tables. Sample-level metric generation, refits and bootstrap calculations can require additional inputs. Figure 5 has score tables and no historical plot export.
- **External or withheld inputs.** Figure 4 needs saved predictions that are outside this candidate. Preprocessing, rolling-origin fits and external comparisons require source data, preprocessing or internal experiment snapshots. The candidate does not provide the seven full forecast CSVs, Figure 1 imagery, archived PDFs, source datasets, model weights, HRES or station results, or the full ECDF.
- **Unverified training scope.** This project does not claim verified full-model retraining, reconstruction of every historical run, or a same-window HRES comparison.

See the [figure and table index](docs/figure_table_map.tsv), [data access and attribution](docs/data.md), and [reproduction guide](docs/reproducibility.md).

## Optional snapshot plotting

Use Python 3.12, the versions in [requirements.txt](requirements.txt), and the TeX dependencies in the reproduction guide. Run from the repository root.

```bash
ESI_PLOT_BACKEND=pgf python code/plot_r1m2.py
ESI_PLOT_BACKEND=pgf python code/plot_r1m3.py
ESI_PLOT_BACKEND=pgf python code/plot_r1m4.py
ESI_PLOT_BACKEND=pgf python code/plot_r2m7.py
```

All four commands completed in a disposable copy of this minimal candidate using the previously verified snapshot environment. Output PDFs are generated locally under `results/figures/revision/`.

## Licence and citation

The Python source code is licensed under [BSD-3-Clause](LICENSE), copyright (c) 2026 Yue Li. The code licence excludes data and scientific result files. See the [data notice](docs/data.md) for the licences and attribution applicable to third-party inputs. Cite Yue Li and Soumyabrata Dev and the manuscript title above. Add a version identifier when a release has been approved and published.
