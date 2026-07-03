# Analysis Methodology

This directory documents the logic and systematic verification processes applied to the provided data pack. To ensure the integrity of the data prior to Copilot indexing, the following audit-based approach was utilized.

## Systematic Approach
In the absence of automated SQL/Python pipelines, a structured data governance framework was applied using spreadsheet-based validation:

1.  **Baseline Profiling**: Identification of key data attributes across `pii_detections`, `license_assignments`, and `site_inventory`.
2.  **Anomaly Detection**: Manual cross-referencing to identify duplicates, inconsistent naming conventions (e.g., department naming variations), and orphan records.
3.  **Data Cleansing**: Application of standardized transformation rules (e.g., ISO 8601 date formatting) to normalize inputs for Copilot compatibility.
4.  **Risk Assessment**: Evaluation of permission structures (anonymous links vs. specific access) against the normalized dataset to determine exposure vectors.

## Tooling
*   **Microsoft Excel / Google Sheets**: Used for data manipulation, pivot-table analysis for anomaly detection, and standardizing date/departmental formats.
*   **Logical Validation**: All cleansing steps were mapped against current Assembly governance standards to ensure recommendations were actionable and compliant.
