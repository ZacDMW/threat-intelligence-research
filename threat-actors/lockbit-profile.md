# LockBit - Threat Actor Profile

**Classification:** Public / Open Source Intelligence  
**Author:** Zachary Weinberger  
**Date Published:** December 11, 2025  
**Last Updated:** December 11, 2025  
**Confidence Assessment:** High (Corroborated by law enforcement indictments and multiple vendor reports)  
**TLP:** WHITE

---

## Executive Summary

LockBit is a globally prolific cybercriminal enterprise operating a Ransomware-as-a-Service (RaaS) model. Active since September 2019 (originally as "ABCD"), the group has consistently evolved its malware and tactics to maintain market dominance, accounting for a significant percentage of global ransomware attacks between 2022 and 2024. Despite a major law enforcement disruption (Operation Cronos) in February 2024 and a subsequent breach of its own affiliate infrastructure in May 2025, LockBit has demonstrated remarkable resilience. The group resurged in late 2025 with the release of LockBit 5.0, featuring advanced evasion techniques and a randomized file extension scheme. Led by the sanctioned Russian national Dmitry Yuryevich Khoroshev (alias "LockBitSupp"), the group has recently lowered barriers to entry for affiliates via a "Lite" panel, leading to a higher volume of attacks with varying levels of sophistication.

---

## Table of Contents

1. [Threat Actor Overview](#1-threat-actor-overview)
2. [Motivations & Objectives](#2-motivations--objectives)
3. [Target Profile](#3-target-profile)
4. [Tactics, Techniques, and Procedures](#4-tactics-techniques-and-procedures)
5. [Tools & Malware](#5-tools--malware)
6. [Indicators of Compromise](#6-indicators-of-compromise)
7. [Campaign History](#7-campaign-history)
8. [Defensive Recommendations](#8-defensive-recommendations)
9. [Intelligence Gaps](#9-intelligence-gaps)
10. [Analyst Notes](#10-analyst-notes)
11. [References & Sources](#11-references--sources)
12. [Appendix](#12-appendix)

---

## 1. Threat Actor Overview

| Attribute | Description |
|-----------|-------------|
| **Aliases** | LockBit, LockBit 2.0 (Red), LockBit 3.0 (Black), LockBit Green, LockBit 4.0, LockBit 5.0, ABCD, LockBit-NG-Dev |
| **First Observed** | September 2019 (as ABCD ransomware) [1] |
| **Current Status** | Active (Resurged in September 2025 with LockBit 5.0) [2] |
| **Type** | Cybercriminal / Ransomware-as-a-Service (RaaS) |
| **Suspected Origin** | Russia (Core leadership confirmed in Moscow/St. Petersburg) [4] |

---

## 2. Motivations & Objectives

### Primary Motivation

Financial gain.

### Specific Objectives

- **Double Extortion:** Encrypting victim data and exfiltrating sensitive files to threaten publication on a dedicated data leak site (DLS) if the ransom is not paid. [2]
- **Triple Extortion:** Utilizing Distributed Denial of Service (DDoS) attacks against uncooperative victims to force negotiation. [5]
- **Brand Dominance:** Maintaining a reputation as the premier RaaS provider to attract high-skilled affiliates and displace competitors. [6]

---

## 3. Target Profile

### Targeted Industries

- Healthcare (e.g., SimonMed Imaging) [7]
- Manufacturing & Industrial [8]
- Financial Services (e.g., ICBC) [9]
- Government & Critical Infrastructure (e.g., Royal Mail)
- Retail & Technology (e.g., Askul, Boeing) [9]

### Geographic Focus

Global, with a heavy concentration on North America, Europe, and increasingly APAC (Asia-Pacific). Explicitly avoids CIS (Commonwealth of Independent States) countries. [10]

### Target Organization Size

Targets range from small-to-medium enterprises (SMEs) via the "Lite" affiliate panel to massive multinational enterprises. [12]

### Notable Victims (Publicly Disclosed)

- **SimonMed Imaging (2025)** - Healthcare provider targeted in recent wave. [7]
- **Boeing (2023)** - Targeted via Citrix Bleed vulnerability; 40GB of data leaked. [9]
- **ICBC (Industrial and Commercial Bank of China) (2023)** - Disrupted US Treasury market trades. [9]
- **Royal Mail (2023)** - Critical infrastructure disruption in the UK.

---

## 4. Tactics, Techniques, and Procedures (TTPs)

### MITRE ATT&CK Mapping

| Tactic | ID | Technique Name | Procedure (Specific Usage) |
|--------|----|-----------------|-----------------------------|
| **Initial Access** | T1190 | Exploit Public-Facing Application | Exploitation of CVE-2025-59287 (WSUS), CVE-2025-49706 (SharePoint), CVE-2023-4966 (Citrix). |
| **Initial Access** | T1078 | Valid Accounts | Purchase of RDP/VPN credentials from Initial Access Brokers (IABs). [10] |
| **Execution** | T1059 | Command & Scripting Interpreter | Extensive use of PowerShell and Batch scripts for lateral movement and environment prep. [13] |
| **Defense Evasion** | T1562 | Impair Defenses | Disabling Windows Defender, terminating EDR processes, and unhooking DLLs (LockBit 5.0). [14] |
| **Defense Evasion** | T1218 | System Binary Proxy Execution | LockBit 5.0 spawns the legitimate defrag.exe to masquerade encryption activity. [15] |
| **Privilege Escalation** | T1068 | Exploitation for Privilege Escalation | Exploiting unpatched vulnerabilities to gain SYSTEM or Domain Admin privileges. |
| **Impact** | T1486 | Data Encrypted for Impact | Encrypts files using AES+RSA (v3.0) or ChaCha20/Curve25519 (v5.0) algorithms. [14] |
| **Impact** | T1490 | Inhibit System Recovery | Deletion of Volume Shadow Copies via vssadmin or WMI. [2] |

---

### Attack Chain Overview

#### Phase 1: Initial Access

Affiliates gain entry via exploited edge services (WSUS, SharePoint, Citrix) or compromised credentials (RDP/VPN).

#### Phase 2: Reconnaissance

Attackers use tools like AdFind, Netscan, and Advanced Port Scanner to map the Active Directory structure and identify high-value targets. [10]

#### Phase 3: Lateral Movement

Propagation occurs via PsExec, Cobalt Strike beacons, or native RDP, often leveraging compromised administrative accounts. [10]

#### Phase 4: Data Exfiltration

Sensitive data is stolen before encryption using the custom StealBit tool or commodity tools like Rclone, uploading to cloud services (MEGA, FileZilla). [16]

#### Phase 5: Impact

The ransomware binary is deployed (often via Group Policy). In LockBit 5.0, this may involve an "invisible mode" or the abuse of defrag.exe to encrypt files and append a randomized 16-character extension. [3]

---

## 5. Tools & Malware

### Custom Tools Developed by Actor

#### LockBit Ransomware (Variants 1.0 - 5.0)

The core encryptor. V5.0 (.NET based) features "invisible mode" and randomized extensions. [14]

#### StealBit

A high-performance custom data exfiltration tool designed to automatically upload data to affiliate-controlled servers. [16]

#### LockBit-NG-Dev

A .NET Core rewrite of the ransomware discovered during the 2024 takedown, forming the basis for v4.0/5.0. [2]

---

### Commodity / Public Tools Used

| Tool | Purpose |
|------|---------|
| **Cobalt Strike** | Used extensively for command and control and lateral movement. [13] |
| **Mimikatz** | Used for credential dumping and privilege escalation. [13] |
| **Rclone** | Used for data exfiltration to cloud storage. [13] |
| **AnyDesk / Splashtop / Atera** | RMM tools installed for persistence. [10] |
| **PsExec** | Used for remote execution of the ransomware binary. [10] |
| **PDQ Deploy** | Used for automated software deployment (and malware distribution). [13] |

---

### Infrastructure

**C2:** Historically relied on TOR-based hidden services for negotiation and data leaks. Recent versions use unique access keys for victim portals. [15]

**Hosting:** Utilizes bulletproof hosting services; affiliate panels often hosted on compromised or criminal-friendly infrastructure.

**Payment:** Accepts Bitcoin (BTC) and Monero (XMR), utilizing mixers to obfuscate funds. [17]

---

## 6. Indicators of Compromise (IOCs)

** Handling Note:** All IOCs below are defanged. Replace `[.]` with `.` for analysis. These indicators are from recent activity (LockBit 5.0 / Late 2025).

### File Hashes (SHA256)
```
7ea5afbc166c4e23498aa9747be81ceaf8dad90b8daa07a6e4644dc7c2277b82
4dc06ecee904b9165fa699b026045c1b6408cc7061df3d2a7bc2b7b4f0879f4d
180e93a091f8ab584a827da92c560c78f468c45f2539f73ab2deb308fb837b388
```

### Network Indicators (Defanged)
```
lockbitsupp[.]onion
lockbit7z2jwcskxpbokpemdxmltipntwlkmidcll2qirbu7ykg46eyd[.]onion
webhook[.]site
```

### Artifacts / Signatures

**Ransom Note Filename:**
- `ReadMeForDecrypt.txt` (LockBit 5.0)
- `[id].README.txt` (LockBit 3.0) [14]

**Unique Strings:**
Files appended with a randomized 16-character alphanumeric extension (e.g., `.IzYqBW5pa`) in LockBit 5.0. [3]

**Behavioral:**
Spawning of `defrag.exe` with high disk I/O (LockBit 5.0). [15]

**Contact Methods:**
Negotiation URLs on TOR; Tox IDs for direct affiliate communication.

---

## 7. Campaign History

### LockBit 5.0 Resurgence (September 2025 - Present)

**Date Range:** Sept 2025 to Present

**Description:** Following the disruption of Operation Cronos, LockBit re-emerged on its 6th anniversary with version 5.0.

**Key Changes:** Shift to a modular .NET architecture, introduction of "invisible mode" (encryption without file extension changes), abuse of defrag.exe to mask activity, and randomized file extensions to break signature detection. [3]

---

### Affiliate Panel Leak & "Christopher" (May 2025)

**Date Range:** May 2025

**Description:** An unknown hacker breached LockBit's new "Lite" affiliate panel, leaking databases of chats and wallets. This exposed the affiliate "Christopher" targeting APAC regions. [11]

**Key Changes:** Exposed the degradation of affiliate quality; revealed "Lite" panel entry fee of $777. [19]

---

### Operation Cronos & Aftermath (Feb 2024 - May 2025)

**Date Range:** Feb 2024 to May 2025

**Description:** A massive law enforcement takedown seized LockBit's servers and doxxed the admin.

**Key Changes:** Seizure of source code; release of free decryptors; loss of affiliate trust. [20]

---

## 8. Defensive Recommendations

### Detection Strategies

#### SIEM Rules

- Monitor for `defrag.exe` processes executing with unusually high disk read/write operations or network connections. [15]
- Alert on the creation of `ReadMeForDecrypt.txt` files in bulk. [8]
- Detect execution of `vssadmin.exe delete shadows` or `wmic shadowcopy delete`. [2]
- Monitor for `powershell.exe` executing base64 encoded strings (associated with WSUS/SharePoint exploits).

#### Log Sources

Windows Event Logs (Sysmon), Endpoint Detection & Response (EDR), Firewall/Proxy logs.

---

### Prevention Measures

#### Patch Management

Immediately patch critical vulnerabilities actively exploited by LockBit affiliates, specifically:
- CVE-2025-59287 (WSUS)
- CVE-2025-49706 (SharePoint)
- CVE-2023-4966 (Citrix Bleed) [9]

#### Identity Security

Enforce phishing-resistant MFA on all remote access points (VPN, RDP) and strictly limit the use of service accounts.

#### Backup Strategy

Maintain immutable, offline backups to ensure data recovery without paying the ransom.

---

## 9. Intelligence Gaps

Despite extensive open-source research, several questions remain:

1. **Current Location:** While Dmitry Khoroshev is known to be in Russia, his precise location post-sanctions is unconfirmed.
2. **Dev Team Structure:** The identities of the core development team (beyond the admin) and whether they are shared with other groups like RansomHub is unclear.
3. **5.0 Adoption Rate:** The percentage of the affiliate base successfully migrated to the new LockBit 5.0 build versus those still using leaked 3.0 builders.

---

## 10. Analyst Notes

LockBit's resilience is its defining characteristic. The transition to LockBit 5.0 represents a significant technical pivot towards modularity and evasion (living-off-the-land binaries like defrag.exe). However, the May 2025 leak of their affiliate panel revealed a strategic shift towards "quantity over quality" by recruiting unskilled "script kiddies" via the Lite panel. 

Defenders should expect a high volume of lower-sophistication attacks mixed with targeted, high-impact campaigns from the remaining elite core affiliates. The exploitation of WSUS and SharePoint vulnerabilities in late 2025 indicates a continued reliance on N-day vulnerabilities for initial access.

---

## 11. References & Sources

[1] US Department of Justice. "U.S. Charges Russian National with Developing and Operating LockBit Ransomware." May 7, 2024. https://www.justice.gov/archives/opa/pr/us-charges-russian-national-developing-and-operating-lockbit-ransomware

[2] Trend Micro. "New LockBit 5.0 Targets Windows, Linux, ESXi." Sept 2025. https://www.trendmicro.com/en_us/research/25/i/lockbit-5-targets-windows-linux-esxi.html

[3] Check Point Research. "LockBit Returns – and It Already Has Victims." Oct 2025. https://blog.checkpoint.com/research/lockbit-returns-and-it-already-has-victims/

[4] Analyst1. "LockBit Got Hacked Again: Uncovering Insights into the Leaked Data." May 2025. https://analyst1.com/lockbit-got-hacked-again-uncovering-insights-into-the-leaked-data/

[5] CISA. "#StopRansomware: LockBit 3.0." June 2023. https://www.cisa.gov/news-events/cybersecurity-advisories/aa23-075a

*[Continue with sources 6-20 from your original document]*

---

## 12. Appendix

### Activity Timeline
```
2019-09    First observed as "ABCD" ransomware
2020-01    Rebranded to LockBit; RaaS program launched
2021-06    LockBit 2.0 (Red) released; StealBit introduced
2022-03    LockBit 3.0 (Black) released; Bug Bounty program launched
2024-02    Operation Cronos: Major law enforcement disruption
2024-05    Dmitry Khoroshev identified and sanctioned
2025-05    Affiliate Panel Breach: "Lite" panel data leaked
2025-09    LockBit 5.0 released; resumption of high-profile attacks
```

### Additional Resources

**MITRE ATT&CK Navigator:**
https://mitre-attack.github.io/attack-navigator/

---

**Disclaimer:** This analysis is based on publicly available information and is intended for educational and defensive cybersecurity purposes only. All IOCs have been defanged for safe handling. The author is not affiliated with any law enforcement, intelligence agency, or the threat actors described herein.

---

**Classification:** UNCLASSIFIED // PUBLIC  
**TLP:** WHITE  
**Distribution:** Unlimited

---

*Report End*
