# State LST Statute Explorer

Statute text and coding for laws on life-sustaining treatment (LST) decisions for incapacitated patients in the 50 US states and Washington, DC. This repository is the data supplement to:

> [Citation for the manuscript, once published]

**[Open the explorer](https://USERNAME.github.io/REPO/statute_explorer.html)**

## What the explorer shows

The map has six views. Four reproduce the manuscript figures, and two map Table 1 domains that have no figure:

- Figure 1A: alternate decision-maker authority over LST decisions
- Figure 1B: withdrawal of artificial nutrition and hydration
- Table 1: alternate decision-maker authority over patient-initiated orders
- Figure 2A: patient revocation of LST instructions
- Figure 2B: contemporaneous patient wishes and objections
- Table 1: patient competence terminology

Click a jurisdiction to read the statute excerpts it was coded on, the code summary for each, and the provisions assigned. Each excerpt names its sheet and row in the codebook. "Look up a provision" outlines every jurisdiction coded for that provision.

Categories within a view are mutually exclusive. A jurisdiction that meets more than one category is shown under the more stringent one, and the legend lists these overlaps.

You can link to a specific view and jurisdiction, for example `statute_explorer.html#view=fig2a&state=NE`.

## Files

| File | Purpose |
|---|---|
| `statutes_and_codes_ha.xlsx` | Codebook. One sheet per domain; each row is jurisdiction, statute text, code summary, provision. |
| `statute_explorer.html` | The explorer. A single self-contained page; no server needed. |
| `explorer_data.R` | Reads the codebook and defines each map view's categories, colors, and expected counts. |
| `build_static_explorer.R` | Rebuilds `statute_explorer.html` from the codebook. |
| `explorer_template.html` | Page layout and script used by the build. |
| `app.R` | The same explorer as a Shiny app, for local use. |

## Rebuilding after a codebook change

```r
Rscript build_static_explorer.R
```

The build prints the count for each map category. If a count no longer matches the expected counts in `explorer_data.R`, it warns and names the view. Update the expected counts once the change is confirmed.

To run the Shiny version instead: `shiny::runApp()` from the repository folder.

Requires R 4.1 or later and the packages readxl, dplyr, tidyr, stringr, viridisLite, sf, usmap (0.7 or later), jsonlite, and here. The Shiny app also needs shiny and ggplot2.

## Sources and limitations

Statute text was taken from official state legislative websites. For Colorado, Georgia, and Tennessee we used the LexisNexis public-access code. For Arkansas and Mississippi we used Justia.

Statutes change. This is research data, not legal advice; check the current official code before relying on any provision.
