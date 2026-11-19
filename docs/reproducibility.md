# Reproducibility

The [figure and table index](figure_table_map.tsv) lists file presence under `included_*`. The other columns record the validation scope and the inputs missing from this minimal candidate.

- **reproducible** means the specified arithmetic check is possible with included inputs, or a PGF redraw was verified in a disposable copy of this candidate.
- **snapshot_only** means an included scientific summary can be inspected. Recreating the underlying output requires additional data or code provenance.
- **partial** means retained evidence covers a subset of an experiment, a prior check used excluded inputs, or the historical output could only be matched in content.
- **not_tested** means the experiment was not rerun in the earlier snapshot verification.
- **blocked** marks a particular missing or unapproved asset.

Table 3's six learning-model rows and Table 5 A1 can be checked by grouping the archived per-seed scores by model and comparing the mean and sample standard deviation to the summaries. The original overall climatology forecast used elsewhere in Table 3 is absent. Table 4 refits its climatology on training targets and needs the regional ERA5 input described in [data.md](data.md).

Figure 5's fixed and validation-selected scores are separate. CSI can be checked as hits divided by forecast events plus observed events minus hits. Prior verification matched 42 fixed and 35 tuned plot values, with minor redraw layout differences. The historical final plotting export is outside this candidate.

Table 5 A1 uses original Gaussian runs. A2 uses q14 W=6 Gaussian runs. B uses separate q11 runs, with dry=0 for the main Tobit and Bernoulli–Gamma configuration. A2 and B retain score summaries. Independent regeneration of case-level scores needs excluded predictions and q11 run metadata, including the dry=0.001 sensitivity inputs for the complete q11 workflow. The full score is a finite-interval numerical integral.

Use [requirements.txt](../requirements.txt) for the earlier Python 3.12 snapshot environment. PGF plotting requires `pdflatex`, `kpsewhich`, Latin Modern and the TeX packages checked by [fig_style.py](../code/fig_style.py). The default rendering path also requires DVI and Poppler tools. The Python snapshot dependencies do not provision TensorFlow/Keras, the XGBoost OpenMP runtime, or a suitable NetCDF backend for every input. Use a disposable working copy for scripts which write into `results/metrics/`.

Historical training and same-window HRES reconstruction are outside the verified workflow. The earlier HRES comparison used a six-hour accumulation proxy against an ERA5 final-hour target.
