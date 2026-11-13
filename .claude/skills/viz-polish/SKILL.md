---
name: viz-polish
description: Use when making or polishing a ggplot2 figure for an audience: a paper, report, poster, slides, or a figure the user calls final. Covers titles, direct labels, color, scales, uncertainty, and saving.
---

# Polishing figures with ggplot2

These are tips for figures meant for an audience. Use the ones that suit the figure, the venue, and the user's request. Polishing changes the presentation and leaves the data unchanged.

## Chart

Start from the chart that worked during exploration. If the comparison that matters is hard to see, consider a different chart before polishing.

## Title and text

- Follow the venue's title style. A title that states the finding often works for slides, posters, and reports. Many journals put a descriptive title in the figure legend and no title on the figure.
- Never invent a finding. Use a descriptive title when the analysis hasn't established a result.
- The subtitle and caption give what was measured, for whom, and when, plus the data source, the sample size, and caveats.
- Axis labels give a plain name and units, such as "Income per person (US dollars, log scale)".

## Labels

- With a few series, label them directly and drop the legend.
- Label the observations that support the point, and leave the rest unlabeled.

## Color

- Use palettes readable with color vision deficiency, such as Okabe-Ito or viridis.
- Pair color with shape, labels, or position, and check the figure in grayscale.

## Scales

- Bars start at zero.
- Panels meant for comparison share axis limits. Note free scales in the caption.

## Uncertainty

- Show uncertainty with the same method and interval level as the analysis. Label a confidence interval as uncertainty in the estimate.

## Theme and saving

- If the project has a theme, use it.
- Set the figure size when saving, then check the saved file.
