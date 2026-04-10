# Phishing & Blocked Outbound Connection

## Overview
This project simulates a SOC L1 investigation involving a phishing email that led to a blocked outbound connection attempt to a suspicious external URL.

The objective is to demonstrate alert triage, threat validation, and escalation decision-making in a SOC environment.


## Scenario
An employee received a phishing email impersonating a delivery service. The email contained a shortened URL designed to trick the user into clicking.

Shortly after, a firewall alert was triggered when the user’s device attempted to access a blacklisted external URL. The connection was successfully blocked.


## Alert Summary

| Field | Value |
|------|------|
| Event ID | 8816 |
| Alert Rule | Access to Blacklisted External URL Blocked |
| Severity | High |
| Data Source | Firewall |
| Action | Blocked |
| Timestamp | Apr 10th, 2026 – 19:55 |


## Affected Entities

- User: Hannah Harris (HR Department)  
- Email: h.harris@company.local  
- Host: win-3457  
- Internal IP: 10.20.2.17  


## Investigation Steps

### 1. Alert Triage
- Reviewed firewall alert indicating blocked outbound connection  
- Identified destination as a blacklisted URL  

### 2. URL Analysis
- URL used a shortened link (bit.ly), commonly used to obfuscate malicious destinations  
- Flagged as suspicious due to phishing patterns  

### 3. Threat Intelligence Check
- Verified IP reputation using browser-based tools (e.g. browserleaks.com)  
- Identified as URL redirection service (bit.ly infrastructure)

### 4. Log Correlation
- Correlated firewall logs with email activity  
- Identified phishing email containing the same URL  

### 5. User Validation
- Verified user identity using internal directory records  
- Confirmed the account belongs to a legitimate employee  


## Outcome

- **Classification:** True Positive  
- **Impact:** Attempted access to malicious URL (blocked)  
- **Status:** Contained (no successful connection observed)  


## Escalation Decision

**Escalated to L2 – Yes**

### Reason:
- Phishing email identified  
- User likely interacted with malicious link  
- Outbound connection attempt observed  
- Requires deeper endpoint analysis  


## Skills Demonstrated

- SIEM alert triage  
- Phishing detection  
- Threat intelligence lookup  
- Log correlation (email + firewall)  
- Incident classification (True Positive)  
- Escalation handling  
