---
name: viz-polish
description: Use when making or polishing a ggplot2 figure for an audience: a paper, report, poster, slides, or a figure the user calls final. Covers titles, direct labels, color, scales, and a project theme. For quick figures to understand data, use viz-explore.
---

# Polishing figures with ggplot2

These are tips for figures meant for an audience. Use the ones that suit the figure, the venue, and the user's request. Polishing changes the presentation and leaves the data unchanged.

## Chart

Start from the chart that worked during exploration. If the comparison that matters is hard to see, consider a different chart before polishing.

## Title and text

- For slides, posters, and reports, a title that states the finding often works well, such as "Infant mortality falls as income rises".
- For journal figures, follow the journal's style. Many journals put a descriptive title in the figure legend and no title on the figure.
- Use a descriptive title when the analysis hasn't established a result.
- A subtitle can give the measure, the population, and the time period.
- A caption can give the data source, the sample size, and caveats such as how missing values were handled.
- Label axes with plain names and units, such as "Income per person (US dollars, log scale)".

## Labels

- Direct labels on lines or points can replace a legend. `ggrepel::geom_text_repel()` helps when labels overlap.
- Label the observations that support the point, and leave the rest unlabeled.
- A short note with `annotate()` can point the reader to what matters. Label any reference lines, such as a clinical threshold.

## Color

- Highlighting one or two groups in a strong color and showing the rest in gray can make the finding easier to see.
- When several categories need their own colors, use a colorblind-safe palette. Ordered values suit a sequential palette.
- Pair color with labels, position, or shape where possible, so the figure still reads in grayscale.

## Scales

- Bars start at zero.
- Panels the reader will compare should use the same axis limits.

## Theme

If the project has a theme, use it.

## Final checks

- The title suits the venue.
- The unit of observation is clear.
- Labels are readable and have units.
- Each axis supports the claim.
