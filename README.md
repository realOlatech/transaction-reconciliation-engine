# Transaction Reconciliation Engine

### Built with Microsoft Excel and Power Query

## Project Overview

The Transaction Reconciliation Engine is an Excel-based solution
designed to compare two transaction datasets---an internal transaction
ledger (Dataset A) and an external statement (Dataset B)---and identify
records that match, contain discrepancies, are missing, or are
duplicated.

The project demonstrates how data preparation, record matching,
validation logic, and interactive reporting can be combined into a
repeatable reconciliation workflow.

## Business Problem

Organisations often maintain transaction records across multiple
systems. Differences between these records can arise from missing
transactions, duplicate entries, inconsistent customer information, or
differences in transaction attributes.

Manually comparing large datasets is time-consuming and can make it
difficult to identify exceptions consistently.

The objective of this project was to build a structured process that
reduces manual comparison effort and makes reconciliation exceptions
easier to identify and investigate.

## Objectives

-   Prepare and standardise two transaction datasets for comparison.
-   Identify duplicate transaction IDs.
-   Match records across datasets using `Transaction_ID`.
-   Compare key transaction attributes and flag discrepancies.
-   Identify records present in one dataset but absent from the other.
-   Produce a consolidated reconciliation report.
-   Present the results in an interactive Excel dashboard.

## Technical Approach

### 1. Data Cleaning and Standardisation

Imported both datasets into Power Query and prepared them for
comparison. This included cleaning text fields, addressing formatting
inconsistencies, and standardising data types and corresponding fields.

### 2. Duplicate Detection

Created duplicate-check queries to identify repeated `Transaction_ID`
values. Duplicate records were flagged for investigation rather than
silently removed from the source data.

### 3. Transaction Matching

Used Power Query Merge operations with `Transaction_ID` as the primary
matching key. A Left Outer Join was used to bring matching Dataset B
information alongside Dataset A records.

A deduplicated lookup query was also prepared for Dataset B to avoid
duplicate IDs multiplying rows during the matching process.

### 4. Field-Level Reconciliation

Created comparison checks for the following transaction attributes:

-   Transaction amount
-   Transaction date
-   Customer name
-   Currency
-   Transaction status
-   Transaction channel

These checks helped distinguish records that matched from those
requiring further investigation.

### 5. Missing Record Identification

Used anti-join logic to identify records that existed in one dataset but
not the other. This supported identification of transactions missing
from Dataset A and transactions missing from Dataset B.

### 6. Reconciliation Classification and Consolidated Reporting

Created reconciliation classifications for matched, mismatched, missing,
and duplicate records.

The results were combined into a final reconciliation report.
Standardised reporting fields were created while retaining the original
source columns and comparison checks to support traceability and
investigation.

### 7. Dashboard Development

Built an Excel dashboard with:

-   KPI cards for key reconciliation metrics
-   A doughnut chart showing reconciliation outcomes
-   A chart showing transaction status distribution
-   A customer slicer for interactive filtering

## Results

The final reconciliation report contained **2,020 records**, classified
as follows:

  Reconciliation outcome                          Records
  ------------------------------------------- -----------
  Matched transactions                              1,788
  Mismatched transactions                             127
  Transactions missing in Dataset B                    60
  Transactions missing in Dataset A                    20
  Duplicate records identified in Dataset B            25
  **Total records in final report**             **2,020**

These figures represent the classifications produced by the project's
reconciliation report. Duplicate records are reported as a
reconciliation category and should be interpreted according to the
report's classification logic.

## Business Value

A workflow of this kind can help organisations:

-   Reduce the effort involved in manual transaction comparisons.
-   Improve visibility into data inconsistencies.
-   Identify missing and duplicate records for follow-up.
-   Support audit and investigation processes through retained source
    values.
-   Produce a repeatable reconciliation report that can be refreshed
    when source data changes.
-   Give stakeholders a high-level view of reconciliation outcomes
    through an interactive dashboard.

## Tools and Techniques

-   Microsoft Excel
-   Power Query
-   Data cleaning and standardisation
-   Merge Queries and Left Outer Join
-   Anti-join logic
-   Duplicate detection
-   Conditional columns and comparison logic
-   PivotTables and PivotCharts
-   Excel slicers and dashboard design

## How to Use

1.  Open the Excel workbook containing the source datasets and Power
    Query solution.
2.  Update or replace the source data while preserving the expected
    column structure.
3.  Refresh the Power Query queries.
4.  Review the final reconciliation report for matched records,
    discrepancies, missing records, and duplicates.
5.  Use the dashboard and customer slicer to explore the results.

*The exact refresh steps depend on how the workbook's source files and
query connections are configured.*

## Project Learning

This project strengthened my practical understanding of data
transformation, Power Query joins, duplicate detection, field-level
validation, reconciliation logic, and dashboard development.

It also reinforced an important principle: data analytics is not only
about presenting data, but also about building practical solutions to
business problems.

<img width="1501" height="693" alt="Screenshot 2026-11-11 143215" src="https://github.com/user-attachments/assets/daa576bc-a9df-4db5-87ff-e10097823e07" />


**Project:** Transaction Reconciliation Engine\
**Tools:** Microsoft Excel \| Power Query\
**Focus:** Data Quality \| Transaction Reconciliation \| Exception
Reporting \| Dashboard Development
