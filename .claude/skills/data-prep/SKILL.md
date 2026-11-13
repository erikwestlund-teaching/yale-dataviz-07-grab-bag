---
name: data-prep
description: Shape data for ggplot2. Use whenever reading, filtering, recoding, reshaping, or summarizing data before plotting.
---

# Data prep for ggplot2

## One row per mark

- Before writing code, say what one point, bar, or line segment is. Shape the data so each row is one of those.

## Aggregate by hand when the stat gets in the way

- When a figure needs means, percentages, or other summaries, compute them first with `group_by()` and `summarize(.groups = "drop")`. Then plot the values as they are with `geom_col()`, `geom_point()`, or `geom_line()`, which use `stat = "identity"`.
- Don't rely on `stat_summary()`, `geom_bar()` counting, or `position = "fill"` to do the math. They make the numbers hard to check, and grouping mistakes go unnoticed.
- Print the summary table before plotting it. The figure should show exactly those numbers.

## Long, not wide

- Columns that hold the same measure for different groups, such as `rate_2020` and `rate_2021`, go long with `pivot_longer()`. Then the group maps to `color`, `fill`, or a facet: one `geom_line()` with `color = series`, never one geom per column.

## Order and labels live in the data

- Set factor order before plotting: `fct_reorder()` to sort by value, `fct_relevel()` for a natural order such as age groups, `fct_infreq()` for counts, and `fct_lump_n()` to collapse many small categories into "Other".
- Recode values into the words the reader should see, such as `"yes"` to "Oil exporter", with `case_when()` or `fct_recode()`. Legends and facet strips then read correctly without extra arguments.

## Missing combinations and missing values

- Use `complete()` to fill in missing group combinations, so dodged bars keep their width and lines don't connect across gaps.
- Count the rows lost to missing values in the plotted variables and report the number. ggplot2 drops them with only a console warning.

## Keep raw units

- Don't log-transform or rescale in the data. Use a scale such as `scale_x_log10()` or `scale_y_continuous(labels = scales::label_percent())`, so the axes show real values.

## Helper data frames for layers

- Build small, separate data frames for highlighted points, labels, and reference lines. Pass each one to its layer with `data =`. Label a filtered subset, not every row.

## Checks

- Run `count()` on every variable mapped to color, fill, or a facet. Too many levels means lumping or a different design.
- Don't modify source data files. Write prepared data to a new object.
