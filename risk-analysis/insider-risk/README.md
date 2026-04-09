# Insider Risk Governance

### Unauthorized Use of Proprietary Teaching Materials

## 📌 Overview

This project analyzes insider risk related to unauthorized access and retention of proprietary teaching materials within a multi-level education program.

The focus is on governance gaps, access control misalignment, and monitoring weaknesses that increase the risk of intellectual property exposure.


## 🎯 Business Objective

Protect proprietary teaching materials while maintaining stable teaching operations.


## ⚠️ Risk Statement

Instructors may download or retain materials beyond assigned levels, especially during resignation periods, leading to intellectual property exposure.


## 🔍 Key Risk Drivers

* Access not consistently limited to assigned teaching levels
* No standardized offboarding or resignation-based access reduction
* Limited visibility into large or unusual download activity
* Inconsistent access control enforcement across branches
* No clearly defined data ownership


## 💥 Business Impact

* Unauthorized reuse of proprietary content
* Competitive disadvantage if program structure is replicated
* Reputational damage if materials are leaked externally
* Operational inconsistency across branches


## 🚨 Governance Gaps

* RBAC (Role-Based Access Control) not aligned with real assignment lifecycle
* No defined threshold for abnormal download behavior
* No regular access review process
* Inconsistent offboarding controls
* Lack of ownership and accountability for monitoring


## 🛡️ Control Strategy (ISMS-Aligned)

### Preventive Controls

* Restrict access to assigned levels (max 6 per month)
* Reduce access within 24 hours of resignation notice
* Stop assigning new levels after resignation
* Limit substitute teaching access to partial materials only

### Detective Controls

* Log all access and download activity
* Flag abnormal or high-volume downloads
* Perform weekly log reviews
* Increase monitoring during resignation periods


## 🎯 Risk Tolerance

Insider misuse cannot be fully eliminated due to legitimate access requirements.
Residual risk is accepted but must be continuously monitored and controlled.


## 📊 Success Metrics

* Access aligned with role assignments after baseline review
* Resignation-based access reduction completed within 24 hours
* All temporary access exceptions documented and approved
* Weekly log reviews consistently completed
* Baseline for misuse incidents established within 30 days
* Measurable improvement tracked over time


## 🧩 Governance Ownership

* **IT**: RBAC implementation, logging, monitoring
* **Academic Operations**: Enforce level-based access rules
* **HR**: Trigger access reduction during resignation
* **GRC / Security**: Monitor risk trends and metrics
* **Data Owner**: Approve access and define acceptable risk


## ⚙️ ISMS Implementation Approach

### Phase 1 - Baseline (Month 1)

* Audit access across all 13 levels
* Identify excessive or inconsistent permissions
* Review past 6 months of download activity
* Evaluate offboarding practices
* Assign clear data ownership

**Outcome:** Current exposure is identified and documented


### Phase 2 - Control Alignment (Months 2–3)

* Define acceptable exposure levels
* Standardize access control across branches
* Formalize resignation-triggered access reduction
* Set thresholds for abnormal download alerts
* Obtain leadership approval

**Outcome:** Consistent and enforceable governance controls


### Phase 3 - Ongoing Monitoring

* Weekly log reviews
* Quarterly risk trend analysis
* Annual policy review
* Continuous KPI monitoring and correction


## 📁 Sample Risk Scenarios (Mini Risk Register)

| Risk ID | Scenario                            | Impact            | Level    | Detection                     | Action                 | Mitigation                   | Owner             |
| ------- | ----------------------------------- | ----------------- | -------- | ----------------------------- | ---------------------- | ---------------------------- | ----------------- |
| IR2.1   | Bulk download for external use      | IP loss           | High     | Unusual download volume       | Restrict + investigate | Set thresholds & alerts      | IT / Academic Ops |
| IR2.2   | Inconsistent access across branches | Unauthorized use  | Med-High | Access beyond assigned levels | Revoke access          | Standardize RBAC             | Academic Ops      |
| IR2.3   | No monitoring ownership             | Undetected misuse | Medium   | No log review                 | Assign ownership       | Define review schedule       | IT / Ops          |
| IR2.4   | Access after resignation            | Data exfiltration | Med-High | Download spikes before exit   | Immediate revocation   | Enforce offboarding controls | HR / IT           |


## 🔥 Key Insight

Access control alone is not enough.
Without lifecycle-based governance and monitoring ownership, legitimate access becomes a primary source of data exposure risk.

