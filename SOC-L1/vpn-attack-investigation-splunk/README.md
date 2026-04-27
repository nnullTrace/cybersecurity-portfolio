# VPN Brute Force & Account Compromise Investigation (Splunk)

## 📌 Scenario

A VPN log dataset was analyzed to identify suspicious authentication activity. This investigation was conducted independently (without predefined lab questions), simulating a real-world SOC analysis workflow.

## 🧩 Notes
* Dataset used is a simulated VPN log file for training purposes
* Analysis focused on detecting real-world attack patterns using Splunk SPL
* Findings were mapped to MITRE ATT&CK techniques to provide structured analysis

## 🔍 Investigation Process
### 1. Identify Failed Login Attempts

```
source="VPNlogs.json" action=failed
| stats count by Source_ip, Username
| sort -count
```

* Found **274 failed login attempts**
* All attempts originated from:

  * **IP:** 172.201.60.191
  * **User:** Simon

  -> Indicates a potential brute force attack targeting a specific account.

![Failed Attempts](images/failed_attempts_by_ip_username.png)

### 2. Compare Failed vs Successful Logins

```
source="VPNlogs.json" UserName="Simon"
| stats count by action, Source_ip
```

* **Failed:** 274 attempts
* **Successful (built):** 4 logins
* All activity came from the same IP address
  -> Confirms brute force attack **resulted in successful authentication**.

![Failed vs Successful Login](images/failed_vs_success_login_activities.png)
 
### 3. Analyze Timeline and Geolocation

```
source="VPNlogs.json" UserName="Simon" action=built
| table _time Source_ip Source_Country
```

* Country: **Canada**
* First successful login:
  * 📅 January 11, 2022 at 07:35 AM
* Subsequent logins:
  * January 12–15, 2022
  * Consistently around **08:35 AM**

  -> Repeated logins occurring at consistent times suggest potential automated or habitual attacker behavior.

![Timeline and Country](images/successful_login_timeline_canada.png)

## 🧩 ATT&CK Mapping
| Stage                | Tactic            | Technique                                                                                               |
| -------------------- | ----------------- | --------------------------------------------------------------------------------------------------------|
| Initial Access       | Credential Access | Brute Force: Password Guessing (T1110.001)                                                              |
| Persistence / Access | Persistence       | Valid Accounts (T1078) - sub-technique not specified due to insufficient evidence regarding account type|

➡️ The attacker gained access via brute force and maintained access using valid credentials without deploying malware

## 🧠 Key Findings
* A single IP (172.201.60.191) targeted a single user (Simon)
* High volume of failed login attempts (274) targeting a single user account indicates brute force activity consistent with password guessing (T1110.001)
* Successful authentication (4 times) confirms account compromise
* Repeated access over multiple days suggests persistent unauthorized access
* Consistent login timing indicates potential automation
* Activity originated from a single geographic location (Canada)


## 🚨 Conclusion
This investigation identified a successful brute force attack, most consistent with Password Guessing (T1110.001), leading to account compromise and persistent unauthorized access via valid credentials (T1078).

The attacker maintained repeated access over several days, indicating ongoing unauthorized presence within the environment. Further investigation is required to determine potential post-authentication activity such as lateral movement or data access.

The attack pattern involved repeated authentication attempts targeting a single user account from a single IP address, which aligns with password guessing behavior rather than password spraying or credential stuffing.


## 🛡️ Recommended Next Steps
### 🔐 Immediate Response
* Reset password for the compromised account
* Enforce Multi-Factor Authentication (MFA)
* Invalidate active sessions

### 🔍 Investigation & Containment
Review post-login activity:
* Resource access
* Internal movement
* Data access or exfiltration
* Monitor or block suspicious IP (172.201.60.191)

### 🚨 Detection Improvements (ATT&CK-aligned)
Alert on:
* High volume of failed login attempts (T1110.001 - Password Guessing)
* Successful login following multiple failures
* Repeated login patterns at consistent times
Implement anomaly detection for:
* Unusual login behavior
* Geographic anomalies

### 🧩 Security Hardening
* Enforce strong password policies
* Enable account lockout thresholds
* Regularly audit inactive or unused accounts

## 🧠 Skills Demonstrated
- Log analysis using Splunk SPL
- Detection of brute force attacks (T1110.001 - Password Guessing)
- Identification of account compromise (T1078)
- Mapping incidents to MITRE ATT&CK
- Incident investigation and response workflow
- Basic threat hunting mindset
