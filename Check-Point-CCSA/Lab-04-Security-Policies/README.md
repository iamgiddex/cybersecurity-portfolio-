# Lab 4: Security Policy Configuration and Network Address Translation

## 1. Overview

This laboratory exercise focused on configuring and organising a Check Point firewall security policy, examining Network Address Translation (NAT), and investigating how firewall rule order affects traffic matching.

The practical work was performed using Check Point SmartConsole and the A-SMS management environment.

**Policy package:** Standard  
**Target gateway:** A-GW-Cluster  
**Gateway members:** A-GW-01 and A-GW-02

## 2. Objectives

The objectives were to:

- Examine the existing security policy.
- Create network objects and configure access control rules.
- Organise firewall rules into logical sections.
- Examine the automatic Hide NAT configuration.
- Investigate the effect of rule ordering.
- Examine policy installation history and identify installation errors.

## 3. Laboratory Environment

| Component | Configuration |
|---|---|
| Management interface | A-SMS |
| Management application | SmartConsole |
| Policy package | Standard |
| Target gateway | A-GW-Cluster |
| Gateway members | A-GW-01, A-GW-02 |
| Internal network | 192.168.11.0/24 |
| DMZ network | 192.168.12.0/24 |
| Web server | 192.168.12.150 |
| Proposed mail server | 192.168.12.151 |
| Management workstation | A-GUI (10.1.1.201) |
| External DNS | Azure-External DNS (168.63.129.16) |

**Environment limitation:** The practical work was restricted to the available A-SMS and SmartConsole interfaces. Direct gateway administration and live traffic verification were not available.

## 4. Task 1: Examination of the Existing Policy

The Standard policy package was selected for the exercise.

On initial inspection, the package contained the default Cleanup rule. This provided the starting point for constructing the access control rulebase.

The existing policy was retained as the basis for the subsequent configuration.

## 5. Task 2: Access Control Policy Configuration

Seven access control rules were created in the Standard policy package. The existing Cleanup rule was also retained and modified.

### 5.1 Configured Rules

| No. | Rule name | Source | Destination | Services | Action | Track |
|---|---|---|---|---|---|---|
| 1 | Admin Access | A-GUI | A-GW-Cluster | SSH, HTTPS | Accept | Log |
| 2 | Stealth Rule | Any | A-GW-Cluster | Any | Drop | Log |
| 3 | Inbound to DMZ | Any | Student-Web-Server, Mail_Server | HTTP, HTTPS, SMTP | Accept | Log |
| 4 | Internal to DMZ | A-INT-NET | Student-Web-Server, Mail_Server | HTTP, HTTPS, SMTP | Accept | Log |
| 5 | DNS Out | A-INT-NET | Azure-External DNS | DNS UDP/TCP | Accept | Log |
| 6 | Internal Web Out | A-INT-NET | Any | HTTP, HTTPS | Accept | Log |
| 7 | SMTP Out | Mail_Server | Any | SMTP | Accept | Log |
| 8 | Cleanup | Any | Any | Any | Drop | Log |

All configured rules were assigned to install on A-GW-Cluster.

### 5.2 Network Objects

The configuration reused available network and host objects where appropriate.

The following existing objects were relevant:

- A-INT-NET
- A-DMZ-NET
- A-GUI
- Student-Web-Server
- Azure-External DNS
- A-GW-Cluster

A mail server object was not available in the existing objects. A proposed host object named `Mail_Server` was therefore created with the IP address `192.168.12.151`.

**Important limitation:** The Mail_Server object represents a proposed policy destination/source. The existence of a functioning mail server at that address was not verified.

### 5.3 Rule 4: Internal to DMZ

The assignment referenced a configuration to be added in Task 5, but the supplied brief did not provide the corresponding Task 5 configuration details.

To complete the practical rulebase exercise, the following proposed configuration was used:

- Source: A-INT-NET
- Destination: Student-Web-Server and Mail_Server
- Services: HTTP, HTTPS and SMTP
- Action: Accept
- Track: Log

This configuration is documented as a proposed implementation decision rather than a configuration explicitly specified by the assignment brief.

### 5.4 Cleanup Rule

The existing Cleanup rule was retained.

Its action was changed to Drop, tracking was set to Log, and the installation target was set to A-GW-Cluster.

## 6. Task 4: Organising the Rulebase into Sections

The configured rules were organised into four logical sections:

| Section | Rules |
|---|---|
| Management and Protection | Admin Access, Stealth Rule |
| DMZ Services | Inbound to DMZ, Internal to DMZ |
| Outbound Access | DNS Out, Internal Web Out, SMTP Out |
| Cleanup | Cleanup |

The sections improved the organisation and readability of the rulebase. They did not change the underlying rule actions or traffic-matching logic.

## 7. Task 6: Network Address Translation

The NAT configuration of A-INT-NET was examined.

Automatically generated Hide NAT rules were visible in the NAT configuration.

The relevant rule showed:

- Original Source: A-INT-NET
- Translated Source: A-NET-NET (Hiding address)

This confirmed that the management configuration contained an automatic Hide NAT rule for the internal network.

**Verification limitation:** Successful live NAT translation could not be established because the security policy could not be installed on the gateway cluster.

## 8. Task 7: Rule Order Experiment and Installation History

### 8.1 Temporary Rule Configuration

A temporary rule named `TEMP Block Internal` was created with the following configuration:

| Field | Value |
|---|---|
| Source | A-INT-NET |
| Destination | Any |
| Services | Any |
| Action | Drop |
| Track | Log |
| Install On | A-GW-Cluster |

### 8.2 Rule Above Internal Web Out

The temporary Drop rule was initially positioned above the Internal Web Out rule.

The policy was published and installation was attempted. Installation failed.

### 8.3 Rule Below Internal Web Out

The temporary rule was moved below Internal Web Out to examine the effect of its position in the rulebase.

The policy was published and installation was attempted again. Installation failed.

### 8.4 Restoration of the Original Rulebase

The temporary rule was deleted, and the original rule order was restored.

The restored rulebase was published.

### 8.5 Installation Failure Investigation

The Installation History showed that policy installation on A-GW-Cluster failed.

The detailed error identified expired gateway VPN certificates on both cluster members.

| Gateway member | Certificate status | Expiration |
|---|---|---|
| A-GW-01 | Expired | 23 May 2026, 07:13:37 |
| A-GW-02 | Expired | 23 May 2026, 07:13:37 |

The error referenced Check Point SK31539.

**Interpretation:** The installation failure was associated with expired gateway VPN certificates. It does not establish that the configured access control rules were invalid.

The temporary rule experiment was completed at the management configuration level. However, because policy installation failed, the practical effect of the two rule positions on live traffic could not be verified.

## 9. Challenges and Limitations

The following limitations affected the practical exercise:

1. **Incomplete assignment instructions:** The supplied brief contained references to Tasks 3 and 5 without corresponding detailed instructions.
2. **Missing mail server object:** A proposed Mail_Server host object was created, but the existence and operational status of the actual server were not verified.
3. **Restricted management access:** The exercise was performed using A-SMS and SmartConsole without direct gateway administration.
4. **Expired gateway certificates:** Both gateway members had expired VPN certificates, preventing successful policy installation.
5. **No live traffic verification:** Access control enforcement, rule matching and NAT translation could not be confirmed through live gateway testing.

## 10. Lessons Learned

The exercise provided practical exposure to:

- Creating and managing firewall network objects.
- Configuring access control rules and services.
- Applying rule ordering and understanding first-match policy evaluation.
- Organising rules into logical sections.
- Examining automatic Hide NAT configuration.
- Using installation history to investigate policy deployment failures.
- Distinguishing management-side configuration from operational gateway verification.

## 11. Conclusion

The Standard policy package was configured with seven new access control rules and an updated Cleanup rule. The rulebase was organised into logical sections, and the automatic Hide NAT configuration was examined.

A temporary Drop rule was used to investigate rule ordering, after which the original rulebase was restored.

Policy installation on A-GW-Cluster was unsuccessful because the VPN certificates on both gateway members had expired. Consequently, the configuration work was completed and documented at the management level, but live policy enforcement and NAT operation remain unverified.

## 12. Supporting Evidence

The complete screenshot evidence for this laboratory is available below:

[View Lab 4 Screenshot Evidence (PDF)](screenshots/CCSA-Lab-04-Screenshot-Evidence.pdf)

