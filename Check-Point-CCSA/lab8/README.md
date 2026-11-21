# Lab 8: HTTPS Inspection

## Summary
On the management server A-SMS, I planned an HTTPS Inspection deployment, created and exported the outbound CA certificate, enabled Full inspection on A-GW-Cluster, built the outbound HTTPS Inspection policy (Bypass Trusted Site above Inspect Outbound), published it and reviewed the Global Settings. The Access Control policy failed to install because the gateway cluster was not running, so the browser tests T1 to T3 were not run.

## Environment
- Management server: A-SMS (10.1.1.101), R82, running
- Gateway cluster: A-GW-Cluster (A-GW-01, A-GW-02), R82, not running (red)
- Log server A-SME and the internal test host were not available

## Outcomes
| Task | Activity | Status |
|---|---|---|
| 1 | Plan the deployment (R82 Release Notes, HTTPS Inspection section) | Completed |
| 2 | Create and export the outbound CA, enable Full inspection | Partly done (CA not installed on a test host) |
| 3 | HTTPS Inspection policy: Bypass Trusted Site (Financial Services) above Inspect Outbound | Completed |
| 4 | Publish | Completed |
| 4 | Install Alpha-Standard on A-GW-Cluster | Attempted, unsuccessful (20-Nov-26 20:38:57) |
| 4 | Tests T1 to T3 | Not run |
| 5 | Review Global Settings (Fail Mode, Categorization Mode, Server Validations) | Completed |
| B | Theory questions (multiple choice, short answer, scenario) | Completed |

## Notes
- Both fail modes are Fail-Open, which lets a connection through uninspected if inspection fails (discussed in the report).
- The report gives the expected test results from the brief and the policy design, not observed results.

## Not verified
- Gateway enforcement of the HTTPS Inspection policy.
- Installation of the CA certificate on a client.
- Tests T1 to T3 (inspected site, bypassed site, client without the CA).

## Files
- [Full report](CCSA108_Lab8_Report.pdf)
