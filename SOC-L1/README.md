# 🔐 SOC L1 Projects
This section showcases hands-on SOC L1 investigations focused on alert triage, log analysis, and incident response.
All projects are based on simulated scenarios but analyzed independently to reflect real-world SOC workflows.

## 🚀 Notes
* All projects are based on **simulated datasets or lab environments**
* The focus is on **analytical thinking and real-world SOC investigation skills**, not just tool usage
* Each project includes queries, evidence (screenshots), and conclusions

## 🎯 Goal
To build practical SOC L1 skills by:
* Investigating real-world attack patterns
* Developing structured analysis workflows
* Practicing detection and response thinking

## 🧠 Skills Demonstrated
* SIEM log analysis (Splunk SPL)
* Threat detection and investigation
* Phishing analysis
* Identification of brute force attacks
* Detection of account compromise and persistence
* Incident classification (True Positive / False Positive)
* Analytical thinking and investigation workflow

## 📂 Projects

### 1. 📧 Phishing & Blocked Outbound Connection

**Event ID:** 8816

* Investigated a phishing email containing a shortened malicious URL
* Correlated email activity with a blocked outbound firewall alert
* Confirmed **True Positive phishing attempt**
* Escalated to L2 for further endpoint analysis

👉 Focus: Alert triage, phishing detection, log correlation, escalation


### 2. 🖥️ Suspicious OneBUpdateService (Persistence Detection)

* Investigated Windows alert for unverified executable
* Identified persistence via **Task Scheduler (OneBUpdate)**
* Validated against legitimate software to avoid false positive
* Removed malicious task and file, no further alerts observed

👉 Focus: Endpoint investigation, persistence detection, remediation

### 3. 🔐 VPN Brute Force & Account Compromise (Splunk)

* Detected **274 failed login attempts** from a single IP
* Identified successful login -> **account compromise (Simon)**
* Observed repeated access over multiple days -> **persistence**

👉 Focus: SPL log analysis, brute force detection, incident investigation


