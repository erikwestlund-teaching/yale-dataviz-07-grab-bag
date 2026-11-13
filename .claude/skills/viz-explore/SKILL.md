---
name: viz-explore
description: Use when plotting data in R to understand it: checking distributions, comparing groups, looking for relationships, trends, or problems. Covers choosing the chart that answers the question and quick, accurate ggplot2 figures.
---

# Exploring data with ggplot2

Exploratory figures are for the analyst and the team. Make many of them quickly, without polishing.

## Setup

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

Avoid dual y axes and 3-D effects. In a stacked bar, only the bottom segment sits on a shared baseline.

When the user asks for a specific figure, draw that figure first. Suggest log scales, smoothers, or other changes as next steps.

## Accuracy checks

- Try more than one histogram bin width, set in the variable's units.
- Box plots hide group size and multiple peaks. With a few hundred points or fewer, overlay the points.
- Consider comparing a straight line with a flexible smoother on scatterplots.
- Reduce overplotting with transparency, smaller points, or 2-D bins.
- Put strongly right-skewed values on a log scale, and say so in the axis label.
- Start bars at zero. Use points when zero isn't meaningful.
- Sort categories by value unless they have a natural order.
- Count the rows ggplot2 drops for missing values before trusting a figure.
