---
name: viz-explore
description: Use when plotting data in R to understand it: checking distributions, comparing groups, looking for relationships, trends, or problems. Covers choosing the chart that answers the question and quick, accurate ggplot2 figures. For figures meant for an audience, use viz-polish instead.
---

# Exploring data with ggplot2

Exploratory figures are for the analyst and the team. Make them quickly, make many, and leave them unpolished.

## Setup

- Set a clean theme once at the top of the notebook with `theme_set(theme_minimal())`, or use the project's own theme.
- Compute counts and summaries in memory. Don't write a new dataset to draw a figure.

## Chart choice

State the question first, one question per figure. Figures or panels the reader will compare should use the same scale, with the same start and end.

| Question | Chart | ggplot2 |
|---|---|---|
| How is one numeric variable distributed? | Histogram | `geom_histogram()` |
| How does a numeric variable differ across groups? | Box or violin plot with the points | `geom_boxplot()`, `geom_violin()`, `geom_jitter()` |
| How many are in each category? | Bar chart, sorted | `geom_col()` or `geom_bar()` |
| How do two numeric variables relate? | Scatterplot | `geom_point()`, `geom_smooth()` |
| How does something change over time? | Line chart | `geom_line()` with `geom_point()` |
| How do estimates compare across many groups? | Dot plot | `geom_point()`, `geom_pointrange()` |
| Does a pattern differ across subgroups? | Small multiples | `facet_wrap()` or `facet_grid()` |

Avoid pie charts, stacked bars for comparing anything but the bottom segment, dual y axes, and 3-D effects.

## Accuracy checks

- Try more than one histogram bin width, set in the variable's units.
- Add the points to box plots when there are a few hundred or fewer.
- Fit both a straight line and a flexible smoother to scatterplots.
- Reduce overplotting with transparency, smaller points, or 2-D bins.
- Use a log scale for skewed values such as income or counts, and say so in the axis label.
- Start bars at zero. Use points when zero isn't meaningful.
- Sort categories by value unless they have a natural order.
- Count the rows ggplot2 drops for missing values.
