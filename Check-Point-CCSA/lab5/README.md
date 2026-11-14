
## Summary
On the management server A-SMS, I created the Orion-Layers policy package and built two Ordered Layers (Orion-Network and Service-Control) and one Inline Layer (DMZ-Policy), then changed and restored the layer order and published each stage. Policy installation on A-GW-Cluster failed four times, so gateway enforcement and the live traffic tests were not verified.

## Environment
- SmartConsole connected to A-SMS (10.1.1.101); target gateway cluster A-GW-Cluster (A-GW-01, A-GW-02)
- Policy package: Orion-Layers (Access Control and Threat Prevention)

## Outcomes
| Task | Activity | Status |
|---|---|---|
| 1 | Explore the default Standard policy and Network layer | Completed |
| 2 | Create Orion-Layers and the Orion-Network layer (five rules) | Completed (configuration only) |
| 3 | Add the Service-Control Ordered Layer | Completed (configuration only) |
| 4 | Install, test and fix (Admin Services rule added) | Attempted, unsuccessful; tests T1 to T5 not performed |
| 5 | Create the DMZ-Policy Inline Layer and attach it to the Internal to DMZ rule | Completed (configuration only), published |
| 6 | Install and verify the Inline Layer | Attempted, unsuccessful; tests T6 to T9 not performed |
| 7 | Reorder the layers, then restore the original order | Completed (configuration only), published; install failed, T3 and T4 not performed |
| 7 | Explain Sharing | Explained; the optional Orion-Branch package was not created |
| B | Theory questions (multiple choice, short answer, scenarios) | Completed |

## Notes
- The generated layer name was already used by an existing layer, so I kept the name Orion-Network instead of renaming it to Network.
- Install Policy Details show expired gateway VPN certificate warnings and a TCP connectivity failure on port 18191 for the cluster members.

## Not verified
- Gateway enforcement of the policy, including the Admin Services correction.
- All nine traffic tests (SSH, HTTP, ping, Telnet, SMTP). The report describes only the expected policy outcomes, not observed results.
- The effect of the layer reordering on matching rules.

## Files
- [Full report](CCSA105_Lab5_Report.pdf)
