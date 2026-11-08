# Lab 1: Check Point Lab Setup and Administration

**Course:** CCSA101 Introduction to Quantum Security
**Student:** Akinsola, Gideon Oluwaferanmi
**Student ID:** C11/26/CCSA/17099
**Completed:** 30 October 2026

## Summary
I built a private management lab around the A-SMS virtual machine in VMware Workstation Pro, connected to it through the Gaia Portal and SmartConsole R82, and explored Gaia and SmartConsole read-only. I changed nothing in the supplied environment.

## Environment
- VMware Workstation Pro 26.0.1; A-SMS VM (8 GB RAM, 8 processors, 500 GB disk, VMXNET3 adapter)
- VMnet8 NAT network 10.1.1.0/24 (NAT gateway 10.1.1.250, DHCP pool 10.1.1.210 to 10.1.1.240)
- Windows host 10.1.1.201; A-SMS eth0 10.1.1.101/24
- Gaia R82 (build 779) and SmartConsole R82

## Outcomes
| Part | Activity | Status |
|---|---|---|
| A | VM, VMnet8, addressing, ping, Gaia Portal, SmartConsole login with fingerprint check | Completed |
| B | Five theory answers (architecture, management services, interfaces, features, evidence) | Completed |
| C | Observation record: Gaia Portal, Clish, Expert mode, SmartConsole (read-only) | Completed |

## Findings recorded (and left unchanged)
- Static default route points to 10.1.1.1, not the NAT gateway 10.1.1.250.
- NTP is not synchronised.
- Two of four licence entries show an expiry date of 30/09/2026.
- A-GW-Cluster, A-GW-01, A-GW-02 and log server A-SME show a red status, consistent with only A-SMS being deployed.

## Not verified
- Internet access from the VM was not tested.
- Nothing was published or installed; no policy changes were made.

## Files
- [Full report](CCSA101_Lab1_Report.pdf)
