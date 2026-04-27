# 🛡️ Incident Analysis: Suspicious OneBUpdateService Blocked by Windows Security

## 📌 Overview

This mini case documents the investigation of a recurring Windows Security alert related to a suspicious executable: `OneBUpdateService.exe`.

The alert indicated that part of the system was blocked due to an unverified application attempting to run.


## 🚨 Initial Alert

* **Source:** Windows Security
* **Message:**
  *"Part of this app has been blocked. We cannot confirm who published OneBUpdateService.exe."*
* **Impact:** Repeated pop-up notifications causing disruption

![Aler](images/alert.png)


## 🔍 Investigation Process

### 1. Check Services

* Opened `services.msc`
* No service named **OneBUpdateService** found
  -> Suspicious (process exists but no registered service)


### 2. Check Task Scheduler

* Opened `taskschd.msc`
* Found task:

  * **Name:** `OneBUpdate`
  * **Action:** Executes suspicious updater file

✅ Identified as persistence mechanism

![OneBUpdate](images/suspicious-task-onebupdate.png)

### 3. File Path Analysis

* Related file:

  * `OneBUpdateService.exe` (unverified publisher)

⚠️ Likely not legitimate due to:

* Unknown origin
* Triggered by scheduled task
* Blocked by Windows Defender


### 4. False Positive Check

* Found similar task:

  * `OneDC_Updater.exe`
* Path:

  * `C:\Program Files (x86)\MSI\MSI_Center_S_Updater\`

✅ Verified as legitimate (MSI software)

🧠 Lesson:

> Similar naming does NOT mean same origin

![False Positive](images/false-positive-onedc-path.png)

## 🧩 ATT&CK Mapping

### Persistence
Technique: Scheduled Task/Job: Scheduled Task (T1053.005)
-> A scheduled task was created using Windows Task Scheduler to repeatedly execute an unverified executable, enabling persistence on the system

### Defense Evasion
Technique: Masquerade Task or Service (T1036.004)
-> The task and executable used naming patterns similar to legitimate update services to avoid detection and user suspicion

## 🧹 Remediation
* Deleted scheduled task: OneBUpdate
* Removed associated executable file
Performed:
* Windows Defender Full Scan
* Microsoft Defender Offline Scan

✅ Result: No further alerts observed after system restart


## 🧠 Key findings
* A scheduled task (OneBUpdate) was used to maintain persistence (T1053.005)
* The associated executable (OneBUpdateService.exe) had no verified publisher
* The file was executed automatically via Task Scheduler
* Naming closely resembled legitimate software, indicating masquerading behavior (T1036.004)
* No corresponding legitimate service was found
* A legitimate MSI updater process was identified and excluded as a false positive


## 🎯 Conclusion
This investigation identified a persistence mechanism using a scheduled task (T1053.005) to execute an unverified executable. The naming convention is consistent with masquerading behavior (T1036.004) used to evade detection.

The threat was successfully removed, and no further malicious activity was observed. This case highlights the importance of validating suspicious processes, distinguishing false positives, and understanding common persistence techniques.


## 🧩 Skills Demonstrated
* Basic incident investigation (SOC Level 1)
* Windows system analysis (Services, Task Scheduler)
* Persistence detection (T1053.005)
* Defense evasion identification (T1036.004)
* Threat validation and false positive analysis
* Incident response and remediation

