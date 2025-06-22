# Week 2 Incident Summary

**Time Period:** July 7 – July 13, 2025
**Total Events:** 4,055 login attempts

**Notable Changes:**
- IP rotation increased significantly
- Attempts from new regions (Brazil, India)
- Payloads now using pastebin links
  
**Mapped Techniques:**
- T1566: Phishing with payload drop
- T1106: Execution via Script
  
**Summary:**
Adversaries attempted new delivery vectors, likely in response to basic
filtering. Recommend setting CloudWatch anomaly detection and further enrichment
with threat intel APIs.
