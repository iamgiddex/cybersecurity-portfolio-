# CCSA105 Lab 5 – Policy Layers (Orion Logistics)

Practical assignment report for **CCSA105 – Policy Layers (Module 5)**, documenting the configuration of Check Point Policy Layers in SmartConsole for the fictional organisation **Orion Logistics**.

## Overview

The lab demonstrates how Check Point Access Control rules can be organised into separate policy layers:

| Layer | Type | Purpose |
|-------|------|---------|
| **Orion-Network** | Ordered Layer | General network access, gateway protection, outbound traffic |
| **Service-Control** | Ordered Layer | Restricts permitted network services |
| **DMZ-Policy** | Inline Layer | DMZ-specific web and mail access, attached to the *Internal to DMZ* rule |

All of these were created inside the **Orion-Layers** policy package.

## What the report covers

**Part A – Practical tasks**
1. Explore the default policy and Network layer (General, Advanced, Permissions, Cleanup Rule)
2. Create the Orion-Layers policy package and build the Network layer
3. Add a second Ordered Layer (Service-Control)
4. Attempt policy installation; add the Admin Services rule
5. Create the DMZ-Policy Inline Layer and attach it to the Internal to DMZ rule
6. Attempt installation of the updated package
7. Reorder layers, restore the original order, and explain Sharing

**Part B – Theory questions:** multiple-choice, short-answer, and scenario questions on Ordered vs Inline Layers, enforcement order, Cleanup Rules, and Sharing.

## Environment and limitations

- **Tools used:** Check Point SmartConsole connected to the Security Management Server (A-SMS).
- **Installation target:** A-GW-Cluster (A-GW-01 and A-GW-02, R82).
- **Policy installation failed** in Tasks 4, 6 and 7. The screenshots show expired gateway certificates and a TCP connectivity failure on port 18191.
- As a result, **live traffic tests (T1–T9) were not performed**, and no gateway enforcement logs were collected. They are recorded in the report as *Not performed*; expected policy outcomes are described as expected logic, not observed results.

Configuration completed in SmartConsole is clearly separated in the report from gateway-dependent activities that could not be verified.

## Repository contents

```
.
├── README.md
├── report/
│   ├── CCSA105_Lab5_Submission_Report_Completed.docx
│   └── CCSA105_Lab5_Submission_Report_Completed.pdf
└── screenshots/            (optional – raw captures, if you choose to include them)
```

## Technologies / topics

Check Point · SmartConsole · Policy Layers · Ordered Layers · Inline Layers · Access Control · Firewall policy · Network security

## Notes

- This repository contains coursework documentation only; there is no source code to build or run.
- Screenshots are genuine captures from the lab environment.

## Author

**[Your Name]** – [Student ID] – [Course / Institution]

## Licence

Documentation © [Your Name]. Shared for portfolio and reference purposes. [Choose a licence, e.g. CC BY-NC 4.0, or "All rights reserved".]
