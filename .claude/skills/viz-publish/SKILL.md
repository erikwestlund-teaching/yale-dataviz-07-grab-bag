---
name: viz-publish
description: Polish a figure for an audience whenever creating a figure for a paper, report, presentation, or slides.
---

# Audience figures

Use this skill for show ponies: workhorse figures polished for an audience. Apply all the exploratory rules below and then add the communication rules.

## Plot choices

- State the question before plotting.
- Pick the chart for the data type and the question.
- Put compared values in position on a common scale.
- Start bars at zero. Use dot plots for means.
- Order categories by value unless they have a natural order.
- Use small multiples on shared axes when groups crowd one panel.
- Show the data behind summaries with points or distributions.
- Use honest scales. Use a labeled log scale for values spanning orders of magnitude.
- Check bin widths and outliers. Inspect unusual values before excluding them.

## Communication

- Write a title that states the finding.
- Use the subtitle and caption to explain measurement, sample size (n), and units. Start the caption with "Source: ".
- Label groups and relevant observations directly instead of using a legend.
- Add text annotations that point the reader to what matters.
- Use color only to highlight. Use the workshop purple (`#7634a6`) for the highlight and `grey70` for the rest. Use a colorblind-safe palette when several groups need their own colors.
- Define a reusable theme function, `theme_yale_workshop()`, once in the notebook's first chunk. Add it to every figure. Build it on `theme_minimal(base_size = 14)`, remove minor gridlines, and use a plain-weight title.
- Save every figure with `ggsave()` at an explicit width, height, and unit in `outputs/figures/`. Create the directory if needed.
- Use associational language. Avoid causal claims and name one limitation.
- Add a `## Style checks` section listing the rules followed. Describe any rule that does not apply to the figure.

## Theme example

```r
theme_yale_workshop <- function() {
  theme_minimal(base_size = 14) +
    theme(
      panel.grid.minor = element_blank(),
      plot.title = element_text(face = "plain")
    )
}
```
