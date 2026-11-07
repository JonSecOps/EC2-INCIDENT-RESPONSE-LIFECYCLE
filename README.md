# EC2 INCIDENT RESPONSE LIFECYCLE

**Project Summary:**

Conducted a cloud-native Digital Forensics and Incident Response (DFIR) investigation into a compromised public-facing Amazon Linux 2023 EC2 instance (Victim-Web-Server). Executed a full PICERL incident response lifecycle to handle a host-level security breach involving unauthorized user creation, root privilege escalation via /etc/sudoers, persistent C2 beaconing via cron jobs, and a localized denial-of-service (DoS) attack through the malicious uninstallation of the Apache web server (httpd).

Rapidly contained the threat using dynamic AWS Security Group manipulation (Forensic-Isolation-SG) to sever outbound C2 traffic while preserving forensic integrity. Performed live host triage to eradicate persistence artifacts and successfully restored business operations by re-provisioning web services and re-establishing safe network controls.

**Learning Points:**

1. **Cloud Network Containment & Security Groups:** Mastered rapid cloud-native isolation techniques by creating dedicated forensic security groups (Forensic-Isolation-SG), cutting off all outbound traffic to neutralize C2 reverse shells while scoping inbound access for responder analysis.
2. **Host-Level Artifact Triage & Discovery:** Investigated linux system integrity by identifying indicators of compromise (IOCs), including unauthorized user accounts (backdoordoor), privilege escalation entries in /etc/sudoers, and malicious scheduled persistence tasks (/etc/cron.d/malicious_job).
3. **Eradication & System Remediation:** Executed precise threat removal protocols, safely stripping unauthorized sudo privileges via visudo, deleting persistent cron mechanisms, and purging rogue system user accounts.
4. **Service Recovery & DoS Mitigation:** Addressed a destructive denial-of-service vector where the threat actor uninstalled core application dependencies, utilizing package managers (dnf) to rebuild the Apache web server environment (httpd) and restore normal operations.
5. **PICERL Incident Response Framework:** Applied a structured, phase-driven methodology (Preparation, Identification, Containment, Eradication, Recovery, and Lessons Learned) to manage a live cloud security incident systematically.
6. **Cloud Telemetry Gaps & Improvements:** Recognized the limitations of host-only triage, establishing the critical need for management-plane visibility through AWS CloudTrail, log parsing via Amazon Athena, and Infrastructure as Code (IaC) automation for rapid incident recovery.
