---
name: viz-explore
description: Use when plotting data in R to understand it: checking distributions, comparing groups, looking for relationships, trends, or problems. Covers choosing the chart that answers the question and quick, accurate ggplot2 figures. For figures meant for an audience, use viz-polish instead.
---

# Exploring data with ggplot2

Exploratory figures are for the analyst and the team. Their job is to show the data accurately so you can understand it. Make them quickly, make many, and don't polish them.

## Setup

- Set a clean theme once at the top of the notebook with `theme_set(theme_minimal())`, or the project's own theme if it has one. Never leave ggplot2's default gray background.
- Compute counts and summaries in memory. Don't write a new dataset just to draw a figure.

## Choose the chart from the question

Say the question first, one question per figure. Position on a common scale is the most accurate way to compare values, so put the values being compared on one shared axis.

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

## Make it accurate

- **Histograms:** try more than one bin width, set in the variable's units. The default 30 bins can hide or invent features.
- **Groups:** a box plot hides group size and multiple peaks. With a few hundred points or fewer, add the points.
- **Relationships:** fit a straight line and a flexible smoother. If they disagree, the relationship isn't linear.
- **Overplotting:** lower transparency, use smaller points, or bin in 2-D.
- **Skewed variables:** use a log scale for values such as income or counts, and say so in the axis label.
- **Bars:** start at zero. When zero isn't meaningful, use points.
- **Order:** sort categories by value unless they have a natural order.
- **Missing values:** ggplot2 drops them with a warning. Count what was dropped before trusting the figure.
- **Unusual values:** look at them and say which observations they are before excluding anything.

## Keep it plain

- Label axes with readable names and units. Variable names are not labels.
- No titles, annotations, or custom colors. That's polishing.
- After each figure, write one sentence on what it shows and anything odd.
- Don't save exploratory figures unless someone needs the file.
