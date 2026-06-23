# Investigation Notes

## Overview

This document records findings from the Apache Suspicious User-Agent Investigation.

---

# Dataset Information

| Field | Value |
|---------|---------|
| Log Source | Apache Access Logs |
| SIEM | Splunk Enterprise |
| Index | main |

---

# Queries Executed

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

## Top Source IPs

```spl
index=main
| stats count by clientip
| sort -count
```

---

# Findings

## Most Common User-Agent

```text
Document Results
```

## Suspicious User-Agents

```text
Document Results
```

## Automated Tools Identified

```text
Document Results
```

## Top Source IPs

```text
Document Results
```

---

# Analyst Assessment

Determine whether activity represents:

- Normal Browsing
- Search Engine Crawling
- Automated Scanning
- Suspicious Web Activity

---

# Conclusion

Summarize findings and recommended next steps.
