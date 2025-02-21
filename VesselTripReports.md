# Vessel Trip Reports 

All electronic VTRs work basically the same way:

1. The vessel operator submits their report using an app. 
2. An EDDI validation in AWS Cloud checks the trip report.
3. The data is added to a queue and sent to the Oracle Database.
4. The data can be used by Fishery Management and others.

This entire process only takes a few seconds. It eliminates the need for sorting, data entry, manual audits, and issues with incomplete or illegible reports. 

``` mermaid

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

A["Vessel Operator"] -- fills out report --> B["FishOnline App"] -- submitted to --> C[("AWS Database")] 
-- passes EDDI validation --> D[("Oracle Database")]
C -- fails EDDI validation --> B -- error notification --> A

```

The FishOnline app sends the data to AWS Cloud, where the data is quickly validated by electronic document data interface (EDDI). On a failure, the AWS sends a message to the VTR app, which displays an error to the user. The user must then correct the errors and resubmit the report. Once a report passes EDDI validation, the data is forwarded to the Gloucester Oracle Database. 

