# [Threat Actor Name] - Threat Actor Profile

| **Attribute** | **Details** |
| :--- | :--- |
| **Author** | Zachary Weinberger |
| **Date Created** | [YYYY-MM-DD] |
| **Last Updated** | [YYYY-MM-DD] |
| **Confidence Level** | **Medium** (Based on open-source intelligence) |
| **TLP** | WHITE |

---

## Executive Summary
[Insert Executive Summary Here]

---

## 1. Threat Actor Overview

| Attribute | Description |
| :--- | :--- |
| **Aliases** | [e.g., LockBit, LockBit 2.0, LockBit Black] |
| **First Observed** | [Date/Year] |
| **Current Status** | [Active / Inactive / Disrupted] |
| **Type** | [e.g., Cybercriminal / Nation-State APT / Hacktivist] |
| **Suspected Origin** | [Country/Region] |

## 2. Motivations & Objectives

* **Primary Motivation:** [e.g., Financial gain, Espionage, Ideological]
* **Specific Objectives:**
    * [Objective 1 - e.g., Financial extortion through double-extortion]
    * [Objective 2]

## 3. Target Profile

* **Targeted Industries:**
    * [e.g., Healthcare]
    * [e.g., Manufacturing]
* **Geographic Focus:** [e.g., Global, North America, avoids CIS countries]
* **Target Organization Size:** [e.g., Enterprise, SME, Government]
* **Notable Victims (Publicly Disclosed):**
    * [Victim 1] (Year) - [Link to disclosure]
    * [Victim 2] (Year)

## 4. Tactics, Techniques, and Procedures (TTPs)

### MITRE ATT&CK Mapping

| Tactic | ID | Technique Name | Procedure (Specific Usage) |
| :--- | :--- | :--- | :--- |
| **Initial Access** | T1078 | Valid Accounts | [Description of how they use this] |
| **Initial Access** | T1566 | Phishing | [Description] |
| **Execution** | T1059 | Command & Scripting Interpreter | [Description] |
| **Persistence** | Txxxx | [Technique Name] | [Description] |
| **Privilege Escalation** | Txxxx | [Technique Name] | [Description] |
| **Defense Evasion** | Txxxx | [Technique Name] | [Description] |
| **Impact** | T1486 | Data Encrypted for Impact | [Description] |

### Attack Chain Overview
1. **Initial Access:** [How they get in]
2. **Reconnaissance:** [What they do first]
3. **Lateral Movement:** [Tools/methods used to move]
4. **Data Exfiltration:** [What they steal and how]
5. **Impact:** [Final objective execution]

## 5. Tools & Malware

### Custom Tools developed by Actor
* [Tool Name] - [Description]
* [Tool Name] - [Description]

### Commodity / Public Tools Used
* [e.g., Cobalt Strike]
* [e.g., Mimikatz]
* [e.g., Rclone]

### Infrastructure
* **C2:** [Description of C2 setup, e.g., TOR usage]
* **Hosting:** [Preferred providers]

## 6. Indicators of Compromise (IOCs)

> **Handling Note:** All IOCs below are defanged. Replace `[.]` with `.` for analysis. These indicators are from recent activity (last 6-12 months).

### File Hashes (SHA256)
```text
[Hash 1]
[Hash 2]
```

### Network Indicators (Defanged)
```text
[IP Address]
[Domain]
[URL]
```

### Artifacts / Signatures
* **Ransom Note Filename:** `[e.g., Restore-My-Files.txt]`
* **Unique Strings:** `[e.g., specific registry keys or mutual exclusions]`
* **Contact Methods:** [Email addresses, TOR Onion links]

## 7. Campaign History

### [Campaign Name / Date]
* **Date Range:** [Start] to [End]
* **Description:** [Brief summary of the campaign]
* **Key Changes:** [e.g., New ransomware variant, new target sector]

## 8. Defensive Recommendations

### Detection Strategies
* **SIEM Rules:** [Suggest logic, e.g., "Monitor for process execution of vssadmin.exe delete shadows"]
* **Log Sources:** [e.g., PowerShell logs, Firewall logs]

### Prevention Measures
* [Recommendation 1 - e.g., Patch management for specific CVEs]
* [Recommendation 2 - e.g., MFA enforcement on VPNs]

## 9. Intelligence Gaps

* [Gap 1 - e.g., Exact relationship between developers and affiliates]
* [Gap 2 - e.g., Full scope of initial access brokers used]

## 10. Analyst Notes

[Insert analysis here. e.g., "This group is increasing the speed of encryption..."]

## 11. References & Sources

1. [Vendor Name]. "[Report Title]." [Date]. [URL]
2. [Agency Name]. "[Advisory Title]." [Date]. [URL]
3. [News Outlet]. "[Article Title]." [Date]. [URL]

---

## Appendix

### Activity Timeline
* **YYYY-MM:** First observed
* **YYYY-MM:** Major event
* **YYYY-MM:** Most recent activity

### Additional Resources
* [Link to MITRE ATT&CK Navigator Layer]
* [Link to Maltego Graph]
