# 🛡️ Cloud Honeypot Project on AWS

This project simulates a real world cloud detection scenario using a public-facing SSH honeypot deployed on AWS EC2. It collects and analyzes malicious activity like brute force login attempts, scanning, and payload drops using Cowrie, GuardDuty, and CloudWatch.

# 🔧 Tools Used
- **Cowrie** – SSH/Telnet honeypot
- **AWS EC2** – Host VM
- **AWS GuardDuty** – Threat detection
- **CloudWatch Logs** – Log aggregation and monitoring
- **GitHub** – Documentation & reporting

# 🧠 Lessons Learned
- Detected over 3,000 SSH login attempts in 7 days
- Analyzed use of common passwords and malware dropper patterns
- Built actionable detection and escalation playbooks

# 📚 Future Improvements
- Add Suricata for network-level visibility
- Enrich findings with external threat intel APIs
