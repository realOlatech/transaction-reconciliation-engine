# Transaction Reconciliation Engine

### Built with Microsoft Excel and Power Query

------------------------------------------------------------------------

# 𝐏𝐫𝐨𝐣𝐞𝐜𝐭 𝐑𝐞𝐩𝐨𝐫𝐭

## 1. Executive Summary

The Transaction Reconciliation Engine is an Excel-based solution
developed to compare two transaction datasets: an internal transaction
ledger (Dataset A) and an external transaction statement (Dataset B).

Built with Microsoft Excel and Power Query, the solution provides a
structured workflow for preparing data, matching transactions,
validating key fields, identifying exceptions, and presenting the
results in a dashboard.

The completed reconciliation report contains **2,020 records** across
five reconciliation classifications. The dashboard also provides a
separate view of transaction statuses---Completed, Pending, and
Reversed---and includes a slicer to filter the connected PivotTables and
charts by transaction status.

## 2. Business Problem

Organisations often maintain transaction records across multiple
systems. Differences between internal and external records can arise
from missing transactions, duplicate entries, or inconsistencies in
transaction details.

Manually comparing large datasets can be time-consuming and makes it
difficult to identify exceptions consistently. Without a structured
process, unresolved differences may be harder to investigate and report.

The objective of this project was to develop a repeatable reconciliation
workflow that makes transaction matching and exception identification
more organised, transparent, and easier to review.

## 3. Project Objectives

-   Prepare and standardise two transaction datasets for comparison.
-   Identify duplicate transaction IDs.
-   Match records across datasets using `Transaction_ID`.
-   Compare key transaction attributes and flag discrepancies.
-   Identify records present in one dataset but absent from the other.
-   Consolidate reconciliation outcomes into a final report.
-   Build an Excel dashboard to communicate the results.

## 4. Data Overview

The project uses two transaction datasets:

  Dataset     Description
  ----------- --------------------------------
  Dataset A   Internal Transaction Ledger
  Dataset B   External Transaction Statement

`Transaction_ID` was used as the primary matching key.

The reconciliation process included comparisons across transaction
amount, transaction date, customer name, currency, transaction status,
and transaction channel.

## 5. Tools and Techniques

**Tools** - Microsoft Excel - Power Query

**Techniques** - Data cleaning and standardisation - Merge Queries and
Left Outer Join - Anti-join logic - Duplicate detection - Conditional
columns and field-level comparison logic - PivotTables and PivotCharts -
Excel slicers - KPI cards and dashboard design

## 6. Methodology and Technical Implementation

### 6.1 Data Cleaning and Standardisation

Imported both datasets into Power Query and prepared them for
comparison. This included cleaning text fields, addressing formatting
inconsistencies, standardising data types, and aligning corresponding
fields.

### 6.2 Duplicate Detection

Created duplicate-check queries to identify repeated `Transaction_ID`
values. Duplicate records were flagged for investigation. A deduplicated
lookup query was also prepared for Dataset B to prevent duplicate IDs
from multiplying rows during the matching process.

### 6.3 Transaction Matching

Used Power Query Merge operations with `Transaction_ID` as the primary
matching key. A Left Outer Join brought matching Dataset B information
alongside Dataset A records.

### 6.4 Field-Level Reconciliation

Created comparison checks for the following transaction attributes:

-   Transaction amount
-   Transaction date
-   Customer name
-   Currency
-   Transaction status
-   Transaction channel

These checks helped distinguish records that matched from those
requiring further investigation.

### 6.5 Missing Record Identification

Used anti-join logic to identify records that existed in one dataset but
not the other. This enabled identification of transactions missing from
Dataset A and transactions missing from Dataset B.

### 6.6 Reconciliation Classification and Consolidated Reporting

Created classifications for matched, mismatched, missing, and duplicate
records. In the final report, transactions missing from Dataset A were
identified as `B-only Transaction`.

The results were combined into a consolidated reconciliation report.
Standardised reporting fields were created while retaining original
source columns and comparison checks to support traceability and
investigation.

### 6.7 Dashboard Development

Built an Excel dashboard containing:

-   Six KPI cards: Total Transactions, Matched, Mismatched, Missing in
    B, Duplicate, and Missing in A.
-   A doughnut chart showing the distribution of reconciliation
    outcomes.
-   A horizontal bar chart showing transaction status distribution:
    Completed, Pending, and Reversed.
-   A `Final_Status` slicer to filter the connected PivotTables and
    dashboard visuals by transaction status.
-   Helper cells on the summary sheet to support KPI values that respond
    to PivotTable filtering.

## 7. Results

### 7.1 Reconciliation Outcomes

The final reconciliation report contained **2,020 records**:

  ----------------------------------------------------------------------------
  Reconciliation outcome                     Records           Share of report
  ------------------------ ------------------------- -------------------------
  Matched transactions                         1,788                    88.51%

  Mismatched transactions                        127                     6.29%

  Transactions missing in                         60                     2.97%
  Dataset B                                          

  Transactions missing in                         20                     0.99%
  Dataset A                                          
  (`B-only Transaction`)                             

  Duplicate records                               25                     1.24%
  identified in Dataset B                            

  **Total**                                **2,020**               **100.00%**
  ----------------------------------------------------------------------------

Percentages are calculated against the 2,020 records in the final report
and rounded to two decimal places.

<img width="1535" height="709" alt="image" src="https://github.com/user-attachments/assets/170d35e6-9602-4db6-9be2-65d249871322" />


### 7.2 Transaction Status Summary

The separate transaction-status PivotTable showed:

  Transaction status       Records   Share of report
  -------------------- ----------- -----------------
  Completed                  1,641            81.24%
  Pending                      226            11.19%
  Reversed                     153             7.57%
  **Total**              **2,020**       **100.00%**

The transaction-status summary is a separate view from the
reconciliation classifications. It describes transaction status, while
the reconciliation outcomes describe the result of comparing Dataset A
and Dataset B.

## 8. Key Findings

1.  **Most records were classified as matched.** The 1,788 matched
    transactions represent approximately 88.51% of the final report,
    indicating that the majority of records were aligned under the
    project's matching and comparison rules.

2.  **127 records require discrepancy review.** The mismatched category
    represents approximately 6.29% of the report. These records should
    be examined to determine which transaction attributes differ and
    what corrective action is appropriate.

3.  **80 records were identified as missing across the two datasets.**
    This consists of 60 transactions missing in Dataset B and 20
    transactions missing in Dataset A. These exceptions should be traced
    to the relevant source system and supporting transaction evidence.

4.  **25 duplicate records were identified in Dataset B.** These records
    require review to establish whether they are genuine duplicate
    postings, repeated extracts, or valid records that need further
    explanation.

5.  **The transaction-status profile is predominantly Completed.**
    Completed transactions account for 1,641 records (81.24%), while
    Pending and Reversed transactions account for 226 (11.19%) and 153
    (7.57%) respectively.

6.  **Reconciliation status and transaction status answer different
    questions.** A transaction can be Completed, Pending, or Reversed
    while also having a reconciliation outcome. Keeping these dimensions
    separate makes the report more useful for investigation.

## 9. Business Recommendations

Based on the reconciliation results, the following actions are
recommended:

### 9.1 Investigate Mismatched Transactions

Review the 127 mismatched records at field level. Confirm whether the
differences relate to amount, date, customer, currency, status, or
channel, and correct the source record where appropriate.

### 9.2 Trace Missing Transactions to Their Source

Investigate the 60 records missing in Dataset B and the 20 records
missing in Dataset A. Use transaction references, dates, amounts, and
supporting evidence to determine whether the records were omitted,
delayed, incorrectly recorded, or assigned different identifiers.

### 9.3 Review Duplicate Records in Dataset B

Examine the 25 duplicate records before making adjustments. Confirm
whether they represent duplicate postings or repeated records in the
source extract. Avoid deleting records until the underlying transactions
have been verified.

### 9.4 Establish an Exception Resolution Process

Assign ownership for each exception, document the investigation outcome,
record any adjustment made, and track unresolved items until closure.
This creates an audit trail and helps prevent exceptions from remaining
unresolved.

### 9.5 Strengthen Upstream Data Controls

Review data-entry, transaction-processing, and export procedures that
may contribute to missing records, duplicates, or inconsistent
transaction attributes. Where possible, introduce validation rules and
unique transaction identifiers at the point of capture.

### 9.6 Run Reconciliation Regularly

Refresh the workflow at an agreed frequency and compare new source data
using the same validation rules. Monitor changes in matched and
exception volumes over time to identify recurring issues.

## 10. Business Value

A workflow of this kind can help organisations:

-   Reduce the effort involved in manual transaction comparisons.
-   Improve visibility into data inconsistencies.
-   Identify missing and duplicate records for investigation.
-   Support audit and exception-management processes by retaining source
    values.
-   Produce a repeatable report that can be refreshed when source data
    changes.
-   Give stakeholders a high-level view of reconciliation outcomes
    through an Excel dashboard.

The project demonstrates how spreadsheet and data-transformation tools
can be used to organise a control process and make exceptions more
visible. The workbook supports identification and reporting;
investigation, approval, and correction of exceptions remain business
activities.

------------------------------------------------------------------------

**Project:** Transaction Reconciliation Engine\
**Tools:** Microsoft Excel \| Power Query\
**Focus:** Data Quality \| Transaction Reconciliation \| Exception
Reporting \| Dashboard Development
