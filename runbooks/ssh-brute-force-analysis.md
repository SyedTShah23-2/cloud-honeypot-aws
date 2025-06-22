# Runbook: SSH Brute Force Analysis

## Alert
- Repeated SSH login attempts from public IPs
- Triggered by Cowrie and GuardDuty
  
## Triage Steps
1. Review Cowrie logs for frequency and usernames used
2. Cross-reference IP with abuse databases (AbuseIPDB, VirusTotal)
3. Check for attempted commands (e.g., wget, curl)
4. Flag and document IPs with more than 100 attempts

## Containment
- No response required (honeypot is non-interactive)
- Continue passive collection
## Detection Enhancement
- Add alert in CloudWatch for rate-based login attempts
- Tune GuardDuty threshold for port probing
