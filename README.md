# Analysis of the `penguins` Dataset

A study on the contribution of sex over physical traits for species
classification and body mass regression, using the `penguins` dataset
distributed with `seaborn`.

## Deliverable

- **Report**: `docs/main.pdf`

## What this repo contains

- `penguins_analysis.ipynb` — refactored notebook with the full pipeline and the A/B robustness study.
- `legacy/penguins_original.ipynb` — the original notebook, kept for reference.
- `docs/` — LaTeX sources and figures for the report.

## Main finding

Adding sex to the predictors produces a consistent gain in every model where the effect is measurable. Logistic regression gains between 0.045 and 0.060 in accuracy for species classification. Linear regression and the random forest gain between 0.048 and 0.075 in R² for body mass regression. The sign of the gain is the same across two disjoint training subsets in every case. The decision tree is the only model with no measurable gain, consistent with its ability to recover size-related splits directly from the physical traits.

## Design

The training set is split into two disjoint halves that share the same test set. Every model is trained once per half and evaluated against the same test set. This isolates the effect of sex from the effect of the particular training rows.

## Reproduce

Open `penguins_analysis.ipynb` and run all cells. The notebook loads the dataset from `seaborn`, trains all models, and writes the figures used in the report to `docs/figures/`.

## Origin

This project started as a coursework assignment and was refactored into a standalone technical report. The original notebook is preserved in `legacy/` for comparison.

## License

MIT