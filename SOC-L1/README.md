# 🔐 SOC L1 Projects

This section showcases hands-on SOC L1 investigations focused on alert triage, log analysis, and incident response.
All projects are based on simulated scenarios but analyzed independently to reflect real-world SOC workflows.


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

Simulated SOC L1 investigation involving:

* Phishing email analysis
* Suspicious outbound connection
* Alert triage and validation

👉 Focus:

* Determine if the alert is a True Positive
* Analyze indicators of compromise (IOCs)
* Support escalation decision


### 2. 🖥️ Suspicious Update Service (OneBUpdateService)

Investigation of a suspicious Windows service masquerading as a legitimate update process.

👉 Key Activities:

* Analyzed service behavior and persistence mechanism
* Identified potential masquerading technique
* Evaluated whether the activity was benign or malicious

👉 Focus:

* Endpoint investigation
* Process and service analysis
* Detection of suspicious system behavior


### 3. 🔐 VPN Brute Force & Account Compromise (Splunk)

Independent investigation of VPN authentication logs using Splunk.

👉 Key Findings:

* Detected **274 failed login attempts** from a single IP
* Identified **successful authentication after brute force attempts**
* Confirmed **account compromise (user: Simon)**
* Observed **persistent access over multiple days**

👉 Focus:

* Log analysis using SPL
* Brute force detection
* Account compromise identification
* Timeline and behavioral analysis


## 🚀 Notes

* All projects are based on **simulated datasets or lab environments**
* The focus is on **analytical thinking and real-world SOC investigation skills**, not just tool usage
* Each project includes queries, evidence (screenshots), and conclusions


## 🎯 Goal

To build practical SOC L1 skills by:

* Investigating real-world attack patterns
* Developing structured analysis workflows
* Practicing detection and response thinking
