# Virginia School Attendance Dashboard

An interactive dashboard exploring the relationship between chronic absenteeism
and mathematics performance across Virginia public schools in 2023–2024.

Pick any of Virginia's 131 school divisions from the dropdown and see that
division's schools in a sortable table, a scatter chart of absenteeism vs. math
pass rate with a best-fit line, and the division's averages next to the state
average.

## Findings

- **1,795 schools** in all **131 divisions**, matched by school between the two
  source files.
- Statewide, higher chronic absenteeism goes with lower math pass rates:
  Pearson **r = -0.412**, R-squared **0.170**, p < 0.001 — a moderate negative
  association, stronger than in Prince William County alone (r = -0.327, 95 schools).
- Statewide unweighted school means: **14.56%** chronically absent,
  **70.87%** math pass rate.
- One school is excluded: Key Center (Fairfax County), whose math pass rate is
  suppressed in the source data, so there is no math rate to pair with its
  absenteeism rate.

## Data and method

Source: Virginia Department of Education, School Quality Profiles, 2023–2024 —
`Chronic Absenteeism.csv` and `Accreditation Rates.csv` (via Data export.zip).

- Chronic absenteeism = percentage of students missing 10% or more of enrolled days.
- Math pass rate = percentage passing, Academic Achievement – Math, All Students.
- Files were matched by division and school name.
- Division and state averages shown are unweighted means across schools in the
  dataset. The VDOE-published enrollment-weighted statewide chronic absenteeism
  rate for 2023–24 is 16.1%; it differs because it weights schools by enrollment.
- School-level and correlational: the dashboard shows association, not causation.

## Built with

HTML, CSS, and JavaScript, with Chart.js for the scatter chart. The dashboard is
a single self-contained page (`index.html`) — no server or build step needed.

## View it

Open `index.html` in a browser, or host it free on GitHub Pages: upload it as
`index.html` in a public repository, then enable Pages in the repository settings.

## Statewide analysis in R

The same data, as a companion analysis — doing the statewide version in R
directly addresses the biggest gap on the resume (the first sample was one
county, Prince William, r = -0.327).

- `va-schools-2023-24.csv` — the matched dataset: 1,795 schools, all 131
  divisions, with absenteeism and math pass rate per school.
- `virginia-absenteeism-math-statewide.R` — base R only, no packages needed.
  Run it with this folder as the working directory (`Rscript
  virginia-absenteeism-math-statewide.R`). It prints the statewide
  correlation (r = -0.412, R-squared = 0.170, p < 0.001), the Prince William
  comparison, and writes `va-division-summary-2023-24.csv` plus a scatter
  plot with the regression line (`va-absenteeism-math-scatter-2023-24.png`).
  Expected output is noted in the script header and was verified against
  the same data on 2026-11-20.
