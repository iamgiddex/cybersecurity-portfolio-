# Check Point CCSA R82: Security Operations Monitoring (Lab 06)

**Course:** CCSA106 – Check Point Certified Security Administrator (R82)  
**Module:** Module 6 – Security Operations Monitoring  
**Author:** Gideon Oluwaferanmi Akinsola  
**Date:** 19 November 2026  

---

##  Overview
This repository contains the practical laboratory report and supporting visual evidence for **Lab 06: Security Operations Monitoring**. The objective of this lab is to audit log server storage and retention configurations, investigate firewall traffic using predefined and custom queries, monitor gateway health, and correlate network security logs with administrative audit records.

## Lab Environment & Topology
* **Management Server:** `A-SMS` (`10.1.1.101`, Check Point R82 on Gaia OS)
* **Dedicated Log Server:** `A-SME` (`10.1.1.130`, offline during lab session)
* **Security Gateway Cluster:** `A-GW-Cluster` (`10.1.1.1`) with members `A-GW-01` (`10.1.1.2`) and `A-GW-02` (`10.1.1.3`)
* **Time Zone:** West Africa Time (WAT, `UTC+01:00`)
* **Tools Used:** Check Point SmartConsole, SmartView Web, and SmartView Monitor

---

## Key Findings & Summary

### Lab 6A: Elevate Traffic View & Log Investigation
* **Log Server Review (`A1`):** Inspected `A-SMS`, which acts as the active backup log server in the topology with **Log Indexing** enabled. Disk space alerts trigger below `3000 MB` and old log deletion begins below `5000 MB`.
* **Capacity Planning:** Calculated storage requirements for a `140 GB` budget receiving `4 GB/day` of raw logs and `2 GB/day` of indexes:
  * **14 days indexed logs:** `84 GB`
  * **7 additional days raw logs:** `28 GB`
  * **Total Used:** `112 GB` (leaving `28 GB` / `20%` free buffer)
* **Rule Tracking & Custom Queries (`A2`–`A4`):** Investigated historical traffic from `Admin_PC` (`10.1.1.201`) in SmartView Web. Verified that HTTPS management connections to `A-GW-02` (`10.1.1.3`) were permitted under **Rule 2 ("Security Gateway Access rule")** of the `Alpha-Standard` policy because its Track action is set to **Log**.

### Lab 6B: Monitor System States
* **Gateway Health (`B1`):** Verified cluster status via SmartView Monitor (`Gateways Status > All Gateways`). Confirmed that `A-GW-01`, `A-GW-02`, and `A-SME` were disconnected due to single-VM host resource limits, while `A-SMS` operated normally (`27%` CPU, `5.65 GB` Active Virtual Memory, `85%` Free Disk).
* **Security vs. Audit Logs (`B2`):** Contrasted network-level firewall traffic logs (`Admin_PC` HTTPS access) against management-plane audit logs (`cpadmin` SmartView Web login), demonstrating how both log types correlate administrative changes with network behavior.

---

## Repository Structure
* `report/CCSA106_Lab06_C11-26-CCSA-17099.pdf` – Complete formatted lab report with embedded evidence (`E1`–`E6`).

---

## Lab Constraints & Notes
Due to local host virtualization limits (running one VM at a time), `A-GW-Cluster` and `A-SME` were offline during inspection. Historical firewall logs from **12 April 2026** were analyzed via **SmartView Web** as a workaround when the SmartConsole `SmartLog` service remained in an initializing state.
