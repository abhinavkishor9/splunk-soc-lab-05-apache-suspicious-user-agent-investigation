# splunk-soc-lab-05-apache-suspicious-user-agent-investigation

## Overview

This lab demonstrates how to investigate Apache User-Agent strings using Splunk Enterprise.

User-Agent analysis is commonly performed by SOC analysts to identify search engine crawlers, automated scanners, scripting tools, vulnerability assessment platforms, and suspicious web activity.

The objective of this lab is to analyze User-Agent strings, identify unusual behavior, and develop practical web log investigation skills.

---

# Lab Environment

- Splunk Enterprise
- Apache Access Logs
- Search & Reporting App
- Windows Host

---

# Scenario

The SOC team has observed unusual web traffic patterns and wants to determine whether automated tools, bots, or scanners are interacting with the web application.

As a SOC Analyst, your task is to analyze User-Agent strings and identify suspicious activity.

---

# Objectives

- Analyze User-Agent strings
- Identify automated tools
- Detect scanners and crawlers
- Investigate source IP activity
- Review requested resources
- Develop web threat hunting skills

---

# MITRE ATT&CK Mapping

| Technique | Description |
|------------|------------|
| T1595 | Active Scanning |
| T1595.002 | Vulnerability Scanning |
| T1046 | Network Service Discovery |

---

# Severity

**Medium**

Suspicious User-Agent activity may indicate reconnaissance, automated scanning, or attempted exploitation.

---

# Detection Logic

## Top User-Agents

```spl
index=main
| top useragent
```

## Automated Bots

```spl
index=main
(useragent="*bot*" OR useragent="*crawl*" OR useragent="*spider*")
```

## Command-Line Tools

```spl
index=main
(useragent="*curl*" OR useragent="*wget*" OR useragent="*python*")
```

## User-Agent by IP

```spl
index=main
| stats count by clientip useragent
| sort -count
```

## Top Source IPs

```spl
index=main
| stats count by clientip
| sort -count
```

---

# False Positives

- Googlebot
- Bingbot
- Website monitoring solutions
- Internal vulnerability scans
- Search engine indexing

---

# Recommended Containment

Validate suspicious User-Agent activity, investigate source IPs, review accessed resources, and monitor for continued automated behavior.

---

# Skills Demonstrated

- Splunk SPL
- Web Log Analysis
- User-Agent Investigation
- Threat Hunting
- Apache Log Analysis
- SIEM Operations

---

# Lessons Learned

This lab improves understanding of:

- Automated web traffic
- Scanner identification
- Bot detection
- User-Agent analysis
- Web threat hunting
