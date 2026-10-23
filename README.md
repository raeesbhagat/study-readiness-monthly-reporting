# Study Readiness, Sample Availability, and Monthly Reports

Is there enough usable data to support the next analysis?

This is a public documentation repository for a connected research workstream in Raee Bhagat’s portfolio. It describes methods and decisions from reviewed project materials. It does not contain the original analysis implementation, participant data, or internal research files.

[Portfolio](https://raeeb.dev/) · [Workstream in the project library](https://raeeb.dev/project-library#P13) · [Detailed case study](https://raeeb.dev/projects/reporting)

## Research context

Created views of how much usable data is available for each route, crew, timepoint, and outcome. The scripts count pre/post PVT observations, identify participants meeting baseline and follow-up requirements, track repeat studies, and summarize operational measures for monthly reports. Route-specific sample reports make missingness and eligibility visible before statistical modeling.

## What the workflow produces

Baseline/follow-up counts, repeated-trip tracking, and route-level data-readiness reports.

## Methods and decisions

- Data completeness profiling.
- cohort eligibility.
- distinct participant counts.
- repeated-trip tracking.
- descriptive reporting.
- reporting automation.

## Libraries and tools

`R`, `dplyr`, `tidyr`, `lubridate`, `openxlsx`, `knitr`, `kableExtra`, `R Markdown`, `Excel`.

These tools are associated with the reviewed workstream. This repository is documentation, so it does not install or execute those libraries.

## Analytical structure

**Unit of analysis:** Participant, trip, and measurement, aggregated by route and month only after completion rules are applied.

**Inputs:** Master tracking workbooks, existing metrics summaries, operational program definitions, and endpoint-completion fields.

**Output:** Updated route-by-month metrics, annual summaries, and formatted multi-sheet Excel workbooks.

The following methodological discussion belongs to the broader case study shared by related workstreams; it is not a claim that every component was implemented independently in this workstream.

### Modular orchestration

UPDATE_PILOT_METRICS.R coordinates readers, completion calculations, metric updates, and spreadsheet writing. Separating these responsibilities makes a definition change easier to isolate and inspect.

### Program-specific completion

Different operational programs have different record structures. Dedicated functions calculate complete and incomplete statuses, including Island Hopper-specific handling, rather than assuming one generic rule covers every route.

### Consistent aggregation

Normalized dates, route labels, and record keys support route-by-month summaries. Unique participants, trips, and usable endpoints are counted separately so repeated participation does not inflate the wrong metric.

### Reviewable exports

The workbook-writing code manages multiple tabs and formatting. Reconciliation against source views gives reviewers a way to investigate totals. Original and updated script folders are versions of the same workflow, not independent projects.

## Validation and interpretation

- **Duplicate records:** Detect repeated trip keys before aggregation and distinguish valid repeated participation from duplicate rows.

- **Missing identifiers:** Report incomplete keys rather than grouping all missing identifiers into an apparent participant.

- **Reconciliation:** Check route/month totals against source views and document why distinct participant counts may not sum across groups.

- **Output consistency:** Verify expected tabs, column definitions, completion categories, and date boundaries in the delivered workbook.

**Model or calculation:** Ingest → normalize keys and dates → apply completion rules → aggregate → reconcile → export

Each aggregate needs a declared unit and eligibility rule. Distinct participant counts are not generally additive across months or routes when the same person appears more than once.

## Where the methods transfer

Data-quality assessment, cohort feasibility, and transparent reporting of missingness.

## Evidence and boundaries

This summary describes analytical work and its interpretation. It is not a certification, a causal claim, or evidence of a deployed production service.

The portfolio contains twenty connected workstreams. Several share datasets, preparation logic, research programs, or legacy code. Separate documentation repositories do not imply twenty independent completed studies or exclusive authorship of all underlying research.

## Privacy and reproducibility

- Original datasets, participant identifiers, internal file paths, workbooks, and unpublished source code are not included.
- Public interactive examples on the portfolio use synthetic teaching data and are labeled accordingly.
- There is no install command, runnable research pipeline, or reproducibility claim for this documentation repository.
- No institutional endorsement or ownership of shared research materials is implied.

## Author and contact

Raee Bhagat · [Portfolio](https://raeeb.dev/) · [LinkedIn](https://www.linkedin.com/in/raee-suresh-bhagat-53168890/) · [Email](mailto:raeesbhagat@gmail.com)
