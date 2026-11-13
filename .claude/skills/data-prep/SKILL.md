---
name: data-prep
description: Shape data for ggplot2. Use whenever reading, filtering, recoding, reshaping, or summarizing data before plotting.
---

# Data prep for ggplot2

## Rows

- Shape the data so each row is one point, bar, or line segment.

## Aggregation

- Compute means, percentages, and other summaries with `group_by()` and `summarize(.groups = "drop")` before plotting.
- Plot the summary values with `geom_col()`, `geom_point()`, or `geom_line()`, which use `stat = "identity"`.
- When `stat_summary()`, `geom_bar()` counting, or `position = "fill"` gets confusing, compute the summaries first.
- Print the summary table before plotting it.

## Reshaping

- Pivot columns that hold the same measure for different groups, such as `rate_2020` and `rate_2021`, longer with `pivot_longer()`. Map the group to color, fill, or a facet.

## Factor order and labels

- Set factor order before plotting: `fct_reorder()` to sort by value, `fct_relevel()` for a natural order such as age groups, `fct_infreq()` for counts, and `fct_lump_n()` to collapse small categories into "Other".
- Recode values into reader-facing labels, such as `"yes"` to "Oil exporter", with `case_when()` or `fct_recode()`.

## Missing values

- Fill in missing group combinations with `complete()`.
- Count the rows lost to missing values in the plotted variables and report the number.

## Units

- Keep raw units in the data. Transform with scales such as `scale_x_log10()`.

## Layer data

- Build separate data frames for highlighted points, labels, and reference lines. Pass each one to its layer with `data =`.

## Checks

- Run `count()` on every categorical variable mapped to color, fill, or a facet.
- Leave source data files unchanged. Write prepared data to a new object.
