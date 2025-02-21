# Paper Trip Reports (Historical Context)

GARFO began transitioning to electronic reports in 2018. GARFO no longer accepts paper reports. However, paper reports are still accessible as part of archival database.

Developers working on VTRs and databases should understand how paper reports were structured and processed. Early VTR data structures were based on paper reports.

Let’s briefly review how submitting paper reports worked prior to 2018:

1. Vessel operators fill out and mail paper reports to their regional fishery office.
2. Paper reports are sorted, scanned, and sent to data entry specialists.
3. If any data was incorrect, illegible, or otherwise needed to be audited, a GARFO/NOAA representative would contact the vessel operator, who would correct and resubmit the report.
4. If the report was legible and generally free of errors, the data entry specialists would type up the report and it would be submitted to the database. 

``` mermaid
---
config:
  layout: elk
---
%%{
  init: {
    'themeVariables': {
      'nodeBorder': '#00467F',
      'primaryColor':'#B2292E',
      'lineColor': '#007078'
    }
  }
}%%

flowchart TD
A["Vessel Operator"] -- fills out --> B["Paper Report"] -- mailed to --> C["NOAA Fisheries"] -- processed by --> D["data entry specialists"] -- legible and complete reports --> E[("Oracle Database")]
D -- illegible or incomplete reports --> F["NOAA representative"]
F -- calls about errors --> A

```

This entire process could take anywhere from a few days to a few weeks. It involved dozens of data entry specialists, manual sorting of paperwork, and calling vessel operators.

Due to the slow processing time of paper reports, it can be difficult to cross-reference or audit information submitted by paper. Paper reports had many limitations, such as:

- illegible answers
- invalid permit numbers
- incorrect species codes
- blank or incomplete fields
- extra information submitted but not required

Electronically submitted reports automatically check for many of these issues, reducing these problems. However, modern databases must still account for missing or incomplete fields from archived information from archived paper reports.