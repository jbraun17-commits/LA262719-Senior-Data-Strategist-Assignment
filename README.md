# LA262719-Senior-Data-Strategist-Assignment
## Assignment for Senior Data Strategist

## How to run my work
This repository functions as the Governance Baseline for the upcoming Copilot rollout. To get the most out of these materials, I recommend reviewing them in the logical order of operations outlined below, moving from the identified risk landscape to the proposed policy solutions. 

## Recommended Review Order:
* **Step 1: Understand the Landscape**: Start with the [Cleaned Data and Risk View](https://github.com/jbraun17-commits/LA262719-Senior-Data-Strategist-Assignment/blob/eb40bb3f18dc98f5d4f63373d66b1a4ae888c8e6/output/deliverable-01-cleaned-data-and-risk-review.md). This establishes the baseline truth about our data exposure, including the anomalies found in the initial data pack and the specific high-risk sites (e.g., S-011 and S-022).  
* **Step 2: Review the Strategy**: Proceed to the [Label-Configuration Proposal](https://github.com/jbraun17-commits/LA262719-Senior-Data-Strategist-Assignment/blob/eb40bb3f18dc98f5d4f63373d66b1a4ae888c8e6/governance%20/deliverable-02-label-config.md). This document maps the risks identified in Step 1 to a four-tier sensitivity framework, explaining why we are applying specific protections (e.g., forced encryption for HR data).
* **Step 3: Validate the Labeling Framework**: After reviewing the Label-Configuration Proposal, please examine the [Sample-document labels](https://github.com/jbraun17-commits/LA262719-Senior-Data-Strategist-Assignment/blob/eb40bb3f18dc98f5d4f63373d66b1a4ae888c8e6/output/deliverable-03-sample-document-labels.md). This deliverable applies the proposed sensitivity labels to three distinct test cases (Leadership Pack, Media Release, and Procurement Review) to demonstrate how the classification taxonomy functions on actual Assembly documents.
* **Step 4: Evaluate the Human Impact**: Read the [Ethics Memo](https://github.com/jbraun17-commits/LA262719-Senior-Data-Strategist-Assignment/blob/eb40bb3f18dc98f5d4f63373d66b1a4ae888c8e6/governance%20/deliverable-04-ethics%20memo.md). This outlines the ethical trade-offs of the rollout, specifically explaining why I have advised against the requested targeted monitoring of staff, proposing a more transparent "Enablement" approach instead.
* **Step 5: Check the Rollout Plan**: Finally, review the [Communication & Adoption Plan](https://github.com/jbraun17-commits/LA262719-Senior-Data-Strategist-Assignment/blob/eb40bb3f18dc98f5d4f63373d66b1a4ae888c8e6/output/deliverable-bonus-communication-and-adoption-plan.md). This provides the roadmap for how we will inform staff and measure success during the go-live phase. (Just a little something extra I prepared.)

## Assumptions:
* **Data Integrity**: The provided CSV data pack was a "working draft" and required significant manual cleaning to establish a baseline of truth.
* **Scope**: The analysis assumes a phased rollout, prioritizing high-risk sites (S-006, S-022) before general staff deployment.
* **Technical Constraints**: Recommendations are bounded by current Microsoft 365 licensing (E7) and assume standard sensitivity labeling functionality.

## What I'd do with more time:
### If granted additional time for this project, I would prioritize the following:
1. **Automated Script Validation**: Run dry-run scripts on a sandboxed subset of the S-022 site to measure the impact of bulk-removing anonymous links before executing production-wide.
2. **User-Experience Beta**: Conduct a small-scale survey with the HR and Legal teams (the pilot cohort) to validate whether the proposed "Confidential — People" and "Restricted" labels disrupt critical workflows.
3. **Audit Log Deep Dive**: Analyze 6 months of historical audit logs to correlate over-sharing risks with specific user personas, moving from speculative risk to data-backed behavior patterns.
