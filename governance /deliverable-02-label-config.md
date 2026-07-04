# Deliverable 2: Label-Configuration Proposal
This proposal outlines a structured sensitivity labeling taxonomy designed to address the data exposure risks identified in the baseline audit [cite: 1]. By implementing a four-tier classification system, we ensure granular control over internal and external data flows.
## 1. Proposed Sensitivity Label Hierarchy
The following labels provide a standardized framework for classification across the digital estate. Access rights and protections scale with the sensitivity of the data.

| Label | Configuration & Protection | Primary Use Case |
| :--- | :--- | :--- |
| Public | No encryption. No watermarking. Open sharing enabled. | External-facing documents, press releases, public announcements. |
| Internal | No encryption. Standard audit logging. | General staff communications, operational meeting minutes, team project notes. |
| Confidential — People | Encryption enabled. Permissions restricted to HR and specific department leads. No external sharing. | HR benefits enrolment, payroll records, performance reviews.| 
| Restricted | Strict encryption. No external sharing. No anonymous access. High-priority audit logging for all access events. | Legal opinions, IT architectural risk assessments, strategic planning docs. |


## 2. Targeted Remediation Mapping
Aligning the labels to the specific high-risk sites identified in the "Cleaned Data and Risk View" [cite: 1] ensures that the most vulnerable data is protected immediately upon policy activation.

| Site ID | Proposed Label | Rationale |
| :--- | :--- | :--- |
| S-003 & S-014 | Confidential — People | Forced encryption prevents unauthorized access to PII and SIN bundles detected in these repositories. |
| S-006 | Restricted | Protects privileged legal information; revocation of anonymous links is a prerequisite. |
| S-022 | Restricted (Pending Triage) | Until the site is cleaned, labeling it "Restricted" prevents broad Copilot discoverability. |


## 3. Automated vs. Manual Policy Enforcement
To balance operational efficiency with data security, enforcement will follow a hybrid model:
* **Auto-Labeling (High Precision)**: Use pattern-matching policies to automatically apply the "Confidential — People" label whenever files containing SINs or PII patterns are saved to the environment. This removes the burden of classification from staff for sensitive records.
* **Mandatory Labeling (User-Initiated)**: Apply mandatory labeling policies for new documents created in the "Restricted" site categories. Users must select a classification before the document can be saved, ensuring accountability at the point of origin.
* **Default Policy**: All documents lacking a specific label will default to the "Internal" label to prevent over-sharing while maintaining operational flow.

## 4. Implementation Strategy
1. **Pilot Phase (Week 1)**: Apply policies to a subset of users in HR and Legal to test label application impact on existing workflows.
2. **Full Deployment (Week 3)**: Roll out organization-wide auto-labeling policies.
3. **Review Cycle (Month 1)**: Evaluate label usage statistics and refine auto-labeling thresholds to minimize false positives.
