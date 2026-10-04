# Business Problem

## Background
Amakora Development Bank is a fictional German retail and commercial bank. It provides corporate loans, revolving credit facilities, project finance and commercial mortgages to companies in Germany, other European markets and international markets.

The bank needs to report the financed emissions associated with its lending portfolio. The required data comes from separate sources:

- Loan information comes from the lending systems.
- Company information comes from the counterparty master-data system.
- Company emissions come from company reports and submissions.
- Project financing and project emissions come from project financial statements and project GHG reports.
- Property values and building emissions come from valuation reports, energy records and EPC data.
- An exposure-to-asset map links project finance and mortgage exposures to their underlying asset.
- Exchange rates come from a finance reference table.
- Sector emission factors come from an ESG reference table.
- EU Taxonomy classifications come from a separate mapping table.

## Problem Statement
The bank has no consolidated, auditable view of the financed emissions associated with its lending portfolio.

Loan, counterparty, asset, emissions and classification data are stored in separate sources and contain inconsistent and missing values. This creates a risk of incomplete, inconsistent or non-auditable reporting.

## Project Objective
Consolidate and validate data from all sources, then:

- Convert loan amounts into EUR at the reporting-date exchange rate.
- Select one applicable emissions record per borrower or asset.
- Calculate financed Scope 1 and Scope 2 emissions using PCAF attribution methods by asset class.
- Estimate emissions where an approved estimation method is available.
- Assign an indicative PCAF data-quality score.
- Classify potential EU Taxonomy eligibility.
- Create an exception report for records that fail business rules.
- Produce auditable tables for Power BI reporting.

## Intended Users
- ESG Reporting Manager
- ESG Operations team
- Data Warehouse team
- Data Stewards
- Risk Management
- Internal Audit
- Senior Management

## Decisions Supported
- Whether financed-emissions figures are complete and reliable enough to report.
- Which data gaps to fix first, ranked by the exposure they affect.
- Which borrowers to ask for reported or verified emissions data.
- Which sectors and asset classes drive the portfolio's financed emissions.
- How much exposure cannot yet be screened for EU Taxonomy eligibility because classification data is missing.

## Reporting Scope
- Reporting date: 31 December 2025
- Portfolio: corporate loans, revolving credit facilities, project finance and commercial mortgages in the dataset
- Reporting currency: EUR
- Emissions included: Scope 1 and Scope 2
- Scope 3: available in the source data but excluded from the main financed-emissions KPI
- Emissions approach: reported data is preferred over estimates
- Taxonomy approach: simplified potential-eligibility assessment only
- Taxonomy alignment: not calculated
- Data-quality scale: 1 is the best quality and 5 is the lowest
- Missing data: never converted to zero
- Invalid records: flagged and handled according to documented business rules
- Audit requirement: every important calculation and exclusion must be explainable

## Expected Outputs
- Total valid exposure in EUR
- Financed Scope 1 and Scope 2 emissions
- Economic emission intensity (tCO2e per EUR million)
- Emissions-calculation coverage
- Verified-emissions coverage
- Estimated-emissions share
- Exposure-weighted indicative PCAF data-quality score
- Potentially Taxonomy-eligible exposure
- Number and value of exposures with critical exceptions

## Assumptions
- Exposures are converted to EUR using the rate effective on 31 December 2025; no stale or assumed rates are used.
- Corporate attribution uses EVIC as provided in counterparty master data, capped at 100%.
- Project finance attribution uses total project equity and debt; commercial mortgage attribution uses property value at origination.
- Each project finance or mortgage exposure finances exactly one asset; assets are not shared between exposures.
- Actual origination dates are not available, so all property valuations assume an origination date of 1 January 2020.
- Company emissions records older than three years are treated as stale and replaced by estimation.
- Only company emissions reported on an operational-control boundary are accepted.
- Assured and verified emissions are treated as verified (PCAF score 1); unverified reported emissions score 2.
- Revenue-based sector estimates score 4. Project finance estimates from an ESG data provider also score 4, because the provider's method is not documented.
- Sector emission factors are simplified educational values.

## Limitations
This is a portfolio demonstration, not an official regulatory submission. The institution is fictional and all data is simulated.

The EU Taxonomy component only uses simplified NACE mappings to identify potential eligibility. It does not assess:

- Substantial contribution
- Do No Significant Harm
- Minimum safeguards
- Full Taxonomy alignment

The sector emission factors are simplified educational factors, and the PCAF data-quality scores are indicative.
