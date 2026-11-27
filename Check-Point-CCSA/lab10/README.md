## Summary
On the ICDFA R82 gateway cluster (icdfa-r82-cluster), I recorded the lab baseline, cloned the Optimized Threat Prevention profile, built a pilot rule scoped to the test client, and installed the Threat Prevention policy successfully on the cluster. The baseline connectivity test to the approved internal service did not respond, and I did not complete the Detect and Prevent validation (Task 3), because no protection or approved test procedure had been designated to me.

## Environment
- Management server: icdfa r82 SMS (10.1.1.101), SmartConsole R82; policy package: Standard
- Gateway: icdfa-r82-cluster (members icdfa-r82-cluster1 and icdfa-r82-cluster2), R82
- Test client: my laptop over OpenVPN (10.250.0.120); approved internal service: 10.42.6.4 (TCP port 80 tested)

## Outcomes
| Task | Activity | Status |
|---|---|---|
| 1 | Record gateway, policy package, pilot scope and enabled blades | Completed (the sixth blade is not individually confirmed) |
| 1 | Baseline connectivity to the approved service | Attempted; the service did not respond (cause not established) |
| 2 | Clone Optimized as CCSA110-TP-C11-26-CCSA-17099 | Completed |
| 2 | Pilot rule "CCSA110 Pilot" (scope CCSA110-TestClient, logging, install on the cluster) | Completed |
| 2 | Publish and install Threat Prevention | Completed; installation succeeded on the cluster and both members, 26-Nov-26 20:27:55 to 20:28:08 |
| 3 | Detect and Prevent validation and log comparison | Not completed (see below) |
| 3 | Post-change connectivity check | Not done |
| 4 | Administrator handover note | Completed; recommends keeping the pilot scope |

## Limitations
- Task 3 was not done. I had no instructor-designated protection or approved benign test, and I did not substitute my own. The report lists exactly which evidence is missing and gives the expected Detect and Prevent behaviour, clearly marked as not observed.
- The baseline service did not respond, so no later check could show that normal traffic "still" works.
- I did not capture the Publish step separately, and I did not confirm that the pilot scope matches my VPN address or that rule 1 does not overlap it.

## Files
- [Full report](CCSA110_FinalLab_C11-26-CCSA-17099.pdf)
