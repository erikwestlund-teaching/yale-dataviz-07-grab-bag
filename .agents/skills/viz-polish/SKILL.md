---
name: viz-polish
description: Use when making or polishing a ggplot2 figure for an audience: a paper, report, poster, slides, or a figure the user calls final. Covers titles that state the finding, direct labels, color used to highlight, honest scales, one project theme, accessibility, and saving at the right size. For quick figures to understand data, use viz-explore.
---

# Polishing figures with ggplot2

A polished figure starts as an accurate exploratory figure and adds what a reader needs to understand it without the analyst in the room. Change the presentation, never the data.

## Start from the right chart

Keep the chart that answered the question during exploration. If the comparison that matters isn't on a common scale, fix the chart before polishing it. See viz-explore for choosing a chart.

## State the finding

- **Title:** write the result as a sentence, such as "Infant mortality falls as income rises". A title that only names the variables makes the reader find the point alone.
- **Don't invent a finding.** If the analysis hasn't established a result, use a descriptive title and tell the user.
- **Subtitle:** say what is measured, for whom, and when.
- **Caption:** give the data source, the sample size, and any caveat the reader needs, such as how missing values were handled.
- **Axes:** plain names with units, such as "Income per person (US dollars, log scale)".
- **Claims:** use associational language. Don't imply causation, and name one limitation in the text.

## Label directly

- Put labels next to the lines or points they name, and remove the legend. Use `ggrepel::geom_text_repel()` when labels would overlap.
- Label only the observations that support the point. Labeling every point is clutter.
- Use `annotate()` for a short note where the reader should look. Label reference lines, such as a clinical threshold.

## Use color to highlight

- Give color one job. Show most of the data in a muted gray and the groups the finding is about in one strong color.
- When several categories need their own colors, use a colorblind-safe palette. For ordered values, use a sequential palette.
- Never let color carry information alone. Pair it with labels, position, or shape. The figure should still work in grayscale.

## Keep the scales honest

- Bars start at zero.
- Use the same axis limits across panels the reader will compare. Use free scales only when panels aren't meant to be compared, and say so in the caption.
- Format numbers as percentages, commas, or currency with the scales package.

## Use one theme for the whole project

Define the project's look once as a theme function and add it to every figure. If the project already has a theme, use it. Remove minor gridlines and anything else that doesn't help the reader.

## Size it for where it goes

Set the width, height, and units when saving with `ggsave()`, then open the saved file and check it. Text that is readable on screen can be unreadable at column width.

| Destination | Width × height (inches) |
|---|---|
| Journal, one column | 3.5 × 3 |
| Journal, two columns | 7 × 4.5 |
| Report or web page | 8 × 5 |
| Slide | 10 × 5.6 |

Increase the base text size for slides and posters.

## Check before you finish

- **Point:** do the title and caption make the finding clear?
- **Data:** is it clear what one point or bar is?
- **Labels:** are all labels readable, with units?
- **Scale:** does each axis support the claim honestly?
- **Color:** does color have one job, and does the figure work in grayscale?
- **Size:** is the text readable at the size the figure will be shown?
