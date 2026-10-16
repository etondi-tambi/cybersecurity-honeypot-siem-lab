cybersecurity-honeypot-siem-lab
A cloud-based honeypot lab used to monitor, log, and analyze real-world cyberattacks using SIEM.
Cloud Honeypot & Threat Intelligence Monitoring Lab

Project Overview
This project simulates a cloud-deployed honeypot architecture designed to expose intentionally vulnerable services (such as SSH, RDP, and HTTP) to the public internet. The objective is to capture real-time malicious traffic, aggregate brute-force attack telemetry, and analyze threat actor behavior (such as geolocation, credentials used, and command execution).

---

Architecture & Infrastructure
 Cloud Provider: Microsoft Azure (Resource Group: `honeypot-lab`)
 Honeypot Sensor: Windows / Linux Virtual Machine running telemetry collection agents
 SIEM / Log Aggregation: Microsoft Sentinel / Log Analytics Workspace
 Threat Intelligence Mapping: Integration with GeoIP databases for attack source visualization

---

 Data Flow & Telemetry Pipeline
1. Ingestion: Public-facing virtual machines receive continuous scanning and brute-force attempts from malicious IP addresses globally.
2. Collection: Security event logs (Windows Security Event ID 4624/4625 for failed logins, Linux `/var/log/auth.log`) are streamed directly to a Log Analytics Workspace.
3. Visualization & Alerting: Custom workbooks map attack origins on a geographic coordinate grid based on latitude and longitude extracted from threat intel feeds.

---

 Key Findings & Attack Trends Observed
 Primary Attack Vectors: Automated credential stuffing and brute-force attacks targeting default administrator and root accounts.
 Geographic Distribution: Attack telemetry commonly originates from multiple international ASN blocks scanning for exposed management ports (TCP 22 / TCP 3389).
 Payload Analysis: Attackers frequently attempt automated shell script downloads and post-exploitation reconnaissance immediately following successful brute-force authentication.

---

 Hardening & Defensive Takeaways
 Network Security Groups (NSGs): Restricting inbound management ports to trusted administrative IP ranges drastically reduces unauthorized exposure.
 Just-In-Time (JIT) Access: Implementing JIT VM access ensures ports remain closed until an authorized user requests temporary access.
 Continuous Monitoring: Integrating host logs with a SIEM provides critical visibility into malicious trends before perimeter defenses are breached.

---

 Skills Demonstrated
 Cloud Security & Azure Resource Management
 Honeypot Deployment & Telemetry Collection
 Threat Intelligence Mapping & Log Analysis
 Security Information and Event Management (SIEM) Concepts
