---
name: data-prep
description: Prepare data for a figure. Use whenever reading, filtering, recoding, reshaping, or summarizing data before plotting.
---

# Data preparation for figures

## Before writing code

- Read the codebook in `inputs/raw/`.
- Say what one row represents, and what one row needs to represent for the figure. Reshape or summarize to match.
- Report column types, labels, missing-value codes, and duplicates.

## Rules

- Never change files in `inputs/raw/`.
- Write the preparation as one `dplyr` pipeline with explicit steps. Build paths with `here::here()`.
- Filter to the population the question is about, and report how many rows remain.
- Turn missing-value codes into `NA`. Report how many rows the figure drops for missing values.
- Recode labels into names a reader understands, for example `female` to "Women".
- Make categorical variables factors and set their order: the natural order for ordered categories such as age groups, otherwise by value.
- Keep pre-aggregated values such as percentages as they are. Don't average percentages across groups without weights.

## Checks

- Report the row count before and after each filter.
- Run `count()` on each recoded variable and look for small groups before plotting them.
