# Check Point Certified Security Administrator (CCSA)

## Overview

This repository documents my practical labs for the CCSA course, with one folder per lab.

The labs cover Check Point security administration, including administrator accounts, object management, security policy configuration, policy layers, security monitoring, identity awareness, HTTPS inspection, application control and URL filtering, threat prevention, and Network Address Translation (NAT).

## Course Learning Objectives

By the end of the course, I should be able to:

1. **Introduction to Quantum Security (CCSA101):** Explain the basic concepts of quantum security and why they matter for modern network protection. Build a management lab, explain the three-tier Check Point architecture (SmartConsole, Security Management Server, Security Gateway), and navigate Gaia and SmartConsole.
2. **Administrator Account Management (CCSA102):** Create administrator accounts and permission profiles using least privilege, and publish changes through sessions.
3. **Object Management (CCSA103):** Modify, create and clone network, host and service objects, group them, and publish and install the changes.
4. **Security Policy Management (CCSA104):** Apply the Positive Control Model, build and order an Access Control rulebase, configure NAT, and follow the create, publish, install and verify workflow.
5. **Policy Layers (CCSA105):** Use policy layers to divide a security policy into logical parts and understand how traffic is evaluated across them.
6. **Security Operations Monitoring (CCSA106):** Monitor gateway status, logs and events, and use them to investigate security activity and troubleshoot problems.
7. **Identity Awareness (CCSA107):** Control access based on user and group identity instead of IP addresses alone.
8. **HTTPS Inspection (CCSA108):** Explain and configure inspection of encrypted traffic so threats hidden in HTTPS can be detected.
9. **Application Control and URL Filtering (CCSA109):** Allow or block applications and websites by category to enforce acceptable-use rules.
10. **Threat Prevention Fundamentals (CCSA110):** Describe and configure the core protections that detect and stop malicious traffic.

Across all modules, I also aim to:

- Understand the Check Point management architecture (SmartConsole, Security Management Server and Security Gateways).
- Investigate policy installation errors and apply troubleshooting procedures.
- Document configurations and evidence accurately, and state clearly what was and was not verified.

## Course Modules and Labs

| Lab | Course Code | Course Title | Status |
|---|---|---|---|
| Lab 1 | CCSA101 | [Introduction to Quantum Security](lab1) | Completed (read-only setup and exploration) |
| Lab 2 | CCSA102 | [Administrator Account Management](lab2) | Completed (A-SMS only) |
| Lab 3 | CCSA103 | [Object Management](lab3) | Completed (A-SMS only) |
| Lab 4 | CCSA104 | [Security Policy Management](lab4) | Completed (configuration only); policy installation unsuccessful due to expired gateway certificates |
| Lab 5 | CCSA105 | Policy Layers | Pending |
| Lab 6 | CCSA106 | Security Operations Monitoring | Pending |
| Lab 7 | CCSA107 | Identity Awareness | Pending |
| Lab 8 | CCSA108 | HTTPS Inspection | Pending |
| Lab 9 | CCSA109 | Application Control and URL Filtering | Pending |
| Lab 10 | CCSA110 | Threat Prevention Fundamentals | Pending |

## Tools and Environment

- Check Point SmartConsole
- Check Point Security Management Server (A-SMS)
- Check Point gateway cluster (A-GW-Cluster)

## Documentation Standards

Each lab folder contains its own README and report, covering objectives, environment, implementation steps, configuration evidence, screenshots, troubleshooting, limitations and lessons learned.

## Important Notes

The documented exercises reflect the access available in my laboratory environment. Where gateway installation, live traffic testing or other verification could not be completed, this is stated explicitly in the relevant lab.
