# Cyber Threat Intelligence Research

**Author:** Zachary Weinberger  
**Focus:** Open-Source Threat Intelligence Analysis  
**Started:** December 2025

## About This Repository

Independent cyber threat intelligence research documenting threat actors, campaigns, and malware families. All analysis is based on publicly available information (OSINT) and follows structured analytical techniques.

This repository serves as a portfolio of my CTI work as I transition into the cybersecurity field, specializing in web application penetration testing and cyber threat intelligence.

## Threat Actor Profiles

| Threat Actor | Type | Status | Profile | Last Updated |
| :--- | :--- | :--- | :--- | :--- |
| **LockBit** | Ransomware/Cybercriminal | 🔴 Active | [View Profile](threat-actors/lockbit-profile.md) | Dec 7, 2025 |
| **ALPHV/BlackCat** | Ransomware/Cybercriminal | 🔴 Active | *Coming Soon* | - |
| **Lazarus Group** | Nation-State APT | 🔴 Active | *Planned* | - |

### Legend:
* 🔴 **Active** - Currently conducting operations
* 🟡 **Disrupted** - Temporarily inactive due to law enforcement
* ⚫ **Disbanded** - No longer operational

## Research Statistics

* **Profiles Published:** 1
* **Total Research Hours:** ~15 hours
* **Last Updated:** December 11, 2025
* **Sources Analyzed:** 40+
* **ATT&CK Techniques Mapped:** 25+

## Methodology

All threat actor profiles follow a structured analytical approach:

### Research Process
* **Multi-source verification** - Minimum 3 credible sources for all claims
* **MITRE ATT&CK mapping** - Systematic TTP documentation
* **Confidence assessments** - Explicit confidence levels for all analysis
* **Regular updates** - Profiles updated as new intelligence emerges
* **Ethical OSINT** - All information from publicly available sources

### Quality Standards
* All IOCs defanged for safe handling
* Citations for every claim
* Intelligence gaps explicitly documented
* Analyst bias acknowledged where relevant
* Traffic Light Protocol (TLP) markings applied

## Repository Structure

```text
threat-intelligence-research/
│
├── README.md                      ← You are here
│
├── threat-actors/                 ← Threat actor profiles
│   ├── lockbit-profile.md
│   ├── alphv-profile.md           (coming soon)
│   └── images/
│       └── lockbit-attack-map.png
│
├── campaigns/                     ← Campaign tracking (future)
│   └── [Specific campaign analyses]
│
├── iocs/                          ← IOC collections (future)
│   └── lockbit-iocs.csv
│
├── templates/                     ← Reusable templates
│   └── threat-actor-template.md
│
└── resources/                     ← Research resources (future)
    └── osint-tools.md
```

## Tools & Resources Used

### Analysis Frameworks
* MITRE ATT&CK Framework
* Diamond Model of Intrusion Analysis
* Cyber Kill Chain

### OSINT Tools
* VirusTotal
* URLScan.io
* AlienVault OTX
* Shodan
* Maltego Community Edition
* MISP

### Information Sources
* CISA Advisories
* Vendor Threat Reports (Mandiant, CrowdStrike, Kaspersky, Sophos, Trend Micro)
* The DFIR Report
* BleepingComputer
* Recorded Future
* Ransomware.live

## Learning Journey

This repository documents my progression in cyber threat intelligence as part of my career transition into cybersecurity.

* **Background:**
    * GIAC Foundational Cybersecurity Technologies (GFACT) certified
    * Google Cybersecurity Certificate
    * Multiple Cisco certifications
* **Programming:** Python, JavaScript, Kotlin, SQL
* **Goals:**
    * Master cyber threat intelligence analysis
    * Develop expertise in web application security
    * Build professional portfolio for career entry
    * Contribute to defensive cybersecurity knowledge
* **Current Focus:**
    * Threat actor profiling
    * MITRE ATT&CK framework mastery
    * OSINT techniques
    * Intelligence writing and reporting

## Confidence Levels

All assessments include explicit confidence levels:

| Level | Criteria |
| :--- | :--- |
| **HIGH** | Multiple credible sources, corroborating evidence, verified by authorities |
| **MEDIUM** | Limited sources, some uncertainty remains, logical inference required |
| **LOW** | Single source, unverified, speculative, requires further research |

## Traffic Light Protocol (TLP)

All published research follows TLP standards:

| TLP Level | Description | Usage in This Repo |
| :--- | :--- | :--- |
| **TLP:WHITE** | May be distributed without restriction | All published profiles |
| **TLP:GREEN** | Community-wide distribution | N/A (not applicable for public repo) |
| **TLP:AMBER** | Limited distribution | N/A |
| **TLP:RED** | Personal for named recipients only | N/A |

## Disclaimer

**Important Legal and Ethical Notice:**
This research is for educational and defensive cybersecurity purposes only.

* All information is derived from publicly available sources (OSINT)
* All IOCs are defanged and intended for threat hunting and detection use cases
* This research should **NOT** be used for offensive operations
* The author is not affiliated with any government, law enforcement, or intelligence agency
* The author is not affiliated with any threat actors described herein
* Information is provided "as-is" without warranty of any kind

**Responsible Disclosure:**
If you discover sensitive information or operational security concerns in these profiles, please contact me privately via LinkedIn.

## Contributing

While this is primarily a personal learning portfolio, I welcome:
* Corrections to factual errors (with sources)
* Additional credible sources for existing profiles
* Suggestions for threat actors to profile next
* Feedback on analysis methodology

**Not Accepting:**
* Speculative attribution without evidence
* Operational IOCs without proper defanging
* Information that could harm active investigations

## Connect With Me

I'm actively learning and documenting my journey into cybersecurity. Let's connect:

* **Blog:** [Medium](https://medium.com/@zacdmw85) - Technical writeups and learning journey
* **LinkedIn:** [Zachary Weinberger](https://www.linkedin.com/in/zachary-weinberger/)

## Related Projects

Other repositories in my cybersecurity portfolio:

* **Web Security Projects** - *Coming soon:* PortSwigger Academy solutions and custom tools
* **Penetration Testing Tools** - *Coming soon:* Python scripts for security testing
* **CTF Writeups** - *Coming soon:* Capture The Flag challenge progress and solutions

## Update Schedule

* **New threat actor profile:** Monthly
* **Profile updates:** As significant intelligence emerges
* **IOC updates:** Weekly for active threats
* **Repository maintenance:** Ongoing
* **Last Repository Update:** December 11, 2025

## Milestones

* [ ] Published first threat actor profile (LockBit)
* [ ] Complete 3 comprehensive threat actor profiles
* [ ] Map 5+ threat actors to MITRE ATT&CK
* [ ] Track one active campaign in real-time
* [ ] Present findings at local security meetup
* [ ] Land first CTI analyst role

## Further Reading

**Recommended Resources for CTI Beginners:**
* [The Intelligence Handbook (Recorded Future)](https://www.recordedfuture.com/resources/guides/the-intelligence-handbook-fourth-edition) - Free PDF (Standard Industry Text)* *Intelligence-Driven Incident Response* by Scott Roberts
* [MITRE ATT&CK Documentation](https://attack.mitre.org)
* [Active Countermeasures Threat Hunting Course](https://www.activecountermeasures.com/hunt-training/) - Free
* [The DFIR Report](https://thedfirreport.com/) - Real incident response cases

## License

This work is licensed under Creative Commons Attribution 4.0 International (CC BY 4.0).

**You are free to:**
* Share — copy and redistribute the material
* Adapt — remix, transform, and build upon the material

**Under the following terms:**
* Attribution — You must give appropriate credit and link to the original

## Acknowledgments

**Sources of Inspiration:**
* The DFIR Report community
* MITRE ATT&CK project
* CISA and other government threat intelligence teams
* Countless security researchers sharing their work publicly

**Special Thanks:**
* The cybersecurity community on Twitter/X for sharing knowledge
* Open-source intelligence community for tools and techniques
* Everyone who has published threat research that helped me learn

---
** If you find this research helpful, please consider starring this repository!**

*Last Updated: December 11, 2025* *Next Profile: ALPHV/BlackCat (Target: January 2026)*
