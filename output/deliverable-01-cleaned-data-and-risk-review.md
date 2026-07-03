# Deliverable 1: Cleaned Data and Risk View

This document outlines the data verification process, the steps taken to clean the provided data pack, and a high-level risk view analyzing where Copilot will be able to access sensitive or over-shared content across the Assembly's digital estate.

## 1. Data Verification & Cleaning Log

Applying a system-based approach to data governance ensures that our baseline metrics are accurate before any automated labeling or Copilot indexing occurs. Several anomalies were identified across the provided CSV files.

### A. pii_detections.csv Anomalies

| Observation / Anomaly | Action Taken |
| :--- | :--- |
| Duplicate scan passes for S-003 (SIN, 212 matches). | Removed the duplicate row to prevent double-counting. |
| Invalid match counts: S-099 lists "many" and S-101 has a blank match count. | Excluded these rows from quantitative totals. Flagged S-099 and S-101 for manual rescanning. |

### B. license_assignments.csv Anomalies

| Observation / Anomaly | Action Taken |
| :--- | :--- |
| Duplicate user entries: Aanya Singh is listed under both a.singh@leg.bc.ca and k.singh@leg.bc.ca. | Consolidated to a single active E7 license for a.singh@leg.bc.ca for counting purposes. |
| The claim that All 900 staff are licensed and Copilot-eligible is false. The data contains disabled accounts and E3 service accounts (which do not qualify for Copilot). | Filtered the dataset to count only active accounts with E7 or E5 licenses for the true Copilot-eligible user base. |
| Inconsistent department names: Hansard vs hansard svcs vs HBS vs Hansard Broadcast, IT vs IT Dept, Member Services vs Member Support. | Changed department names to be consistent (Hansard Broadcast, ITD & Member Services). |

### C. site_inventory.csv Anomalies

| Observation / Anomaly | Action Taken |
| :--- | :--- |
| Inconsistent date formatting in last_modified (e.g., YYYY-MM-DD, MM/DD/YYYY, Mon D YYYY). | Standardized all dates to ISO 8601 format (YYYY-MM-DD). |
| Missing labels for S-007 (Member Services Portal) and S-022 (Old Records). | Flagged for immediate triage. S-022 is particularly risky given the lack of a label combined with anonymous links. |
| Duplicate/Similar rows: S-002 and S-013 both represent "ITD Project Plans" for Carlo Munoz, with slightly different item counts. | Merged into a single site record using the higher item count (12,051) as the most recent truth, pending owner verification. |

### D. sharing_links Anomalies

| Observation / Anomaly | Action Taken |
| :--- | :--- |
| Duplicate site_id for S-011 with competing link type. | Merged into a single site record using the company link type. |
| Missing target_external_domain values for S-011 & S-012. | Identified target_external_domain values for each based on given data. |
| S-006 is assigned anonymous link_type but has a target_external_domain. | Changed the link_type to specific. |

## 2. Copilot Risk View & Label Coverage

Copilot relies strictly on existing permissions. If an employee has access to a file, Copilot can index and synthesize it. The following areas represent the highest risk for data overexposure upon go-live.

### Critical Exposure Vectors

* **S-022 (Old Records pre-2015):** Contains 28,900 items, holds an unclassified legacy archive with 3,300 PII bundle detections, has no current sensitivity label, and currently has anonymous links active. This is a massive exposure risk for Copilot.
* **S-011 (General Staff Share):** This site contains 42,110 items, is shared broadly with allstaff@leg.bc.ca, and allows both anonymous and external company links. Any sensitive data dropped here will be immediately indexed and queryable by the entire Assembly via Copilot.
* **S-012 (Constituency Office Files):** Contains 410 PII bundle matches and 96 SIN matches. While it does not have anonymous links, it is accessible via a shared mailbox, increasing the risk of unauthorized lateral access by Copilot if mailbox permissions are too broad.

### Label Coverage Gaps

Currently, the data shows significant gaps in label enforcement:

* Files containing SINs and PII (e.g., in HR Benefits Enrolment S-003 and Payroll Records S-014) are sitting in folders that lack forced encryption.
* Anonymous links exist on sites (S-005, S-006, S-011, S-019, S-022) that house Internal or even Restricted-caliber information (e.g., Legal Opinions Library S-006).

### Next Steps for Go-Live

1. Execute a targeted script to revoke all anonymous sharing links on S-006 (Legal) and S-022 (Legacy).
2. Force apply the Confidential — People label to S-003 and S-014 to immediately encrypt HR and payroll data, thereby preventing unauthorized Copilot access.
3. Exclude S-022 from Copilot indexing entirely until a thorough classification and cleanup pass is completed.
