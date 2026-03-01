# Access Control Incident – Access Log Review & Mitigations

## Scenario
A deposit/payment was initiated from the business to an unknown bank account. Finance reports this was not an error. The payment was stopped in time. This investigation reviews access logs to understand what happened, identify likely threat activity, document access control weaknesses, and recommend mitigations.

## Evidence & Inputs
- Worksheet: `Access control worksheet.pdf`
- Data source: `Accounting exercise.xlsx`
- Artifacts reviewed:
	- Employee directory table (user roster with last access + end dates)
	- Windows-style application/service event log entry (payroll event)

## Key Evidence (What Stands Out)
- The `Legal\Administrator` account added a **payroll event** at **8:29:57 AM** on **10/03/2023**.
- The action originated from:
	- **Computer:** `Up2-NoGud`
	- **IP:** `152.207.255.255`
- Event description indicates a new payroll/bank destination: **“Payroll event added. FAUX_BANK”**.
- In the employee directory, the most likely matching user is **Robert Taylor Jr. (Legal attorney)** with:
	- **Role:** Legal attorney
	- **Employment type:** Contractor
	- **Authorization:** Admin
	- **Start date:** 9/4/2019
	- **End date:** 12/27/2019
	- **IP address:** 152.207.255.255
	- **Last access:** 8:29:57 AM (5 days ago)

## Timeline of Events
| Date | Time | Account | Action | Source | Notes |
|---|---|---|---|---|---|
| 10/03/2023 | 8:29:57 AM | `Legal\Administrator` | Payroll event added | `Up2-NoGud` / `152.207.255.255` | Destination listed as `FAUX_BANK` |

## Findings
### Potential threat actor indicators
- **Account used:** `Legal\Administrator` (maps to a user shown as no longer employed)
- **Source IP:** `152.207.255.255`
- **Host/computer name:** `Up2-NoGud`
- **High-risk action:** payroll modification / new bank destination (`FAUX_BANK`)

### What likely happened (evidence-based working theory)
A former employee/contractor’s privileged account remained active after termination. That account was then used to add or modify payroll banking details ("FAUX_BANK"), enabling a fraudulent deposit/payment attempt. The organization prevented loss by stopping the payment, but the underlying access control weaknesses remain.

## Access Control Issues Observed
### Authorization issues
- **Excess privilege:** the `Legal\Administrator` account retained privileged payroll modification permissions.
- **Lack of privileged-action safeguards:** a single admin account was able to add a payroll event without requiring additional approval.

### Account lifecycle / offboarding issues
- **Terminated account still active:** the directory lists an **end date (12/27/2019)**, yet the account had **recent access** and executed a payroll action.

### Additional directory red flags (secondary)
The employee directory includes other users with past end dates but recent access, which may indicate broader offboarding/process issues (e.g., accounts not promptly disabled or directory fields not maintained).

## Recommended Mitigations
### Process & governance
- **Mandatory offboarding checklist:** require immediate account deactivation upon employee/contractor termination (HR → IT handoff with confirmation).
- **Periodic access reviews:** perform scheduled audits to validate employment status and privileged access approvals.

### Access control design
- **RBAC + least privilege:** restrict payroll-modification privileges to specific roles; remove admin permissions from users who do not require them.
- **Segregation of duties (SoD):** require dual approval for sensitive payroll changes (new payee/bank destination, payroll event creation).

### Detection & monitoring
- **Alerting:** create alerts for activity by terminated/deactivated accounts and for sensitive payroll events.
- **Privileged logging:** ensure privileged actions include account, time, source IP/host, and are retained for investigation.

## Residual Risk & Follow-ups
- **Residual risk:** If other terminated accounts remain active, similar attempts may recur.
- **Follow-ups:**
	- Validate whether `Legal\Administrator` is tied to a shared account; eliminate shared credentials if present.
	- Confirm whether `Up2-NoGud` is a managed corporate device; investigate if it is unknown/unmanaged.
	- Review other directory entries with end dates to confirm appropriate account status.

## Appendix
### Employee Directory (Provided Table)
| Name | Role | Email | IP address | Status | Authorization | Last access | Start date | End date |
|---|---|---|---|---|---|---|---|---|
| Lisa Lawrence | Office manager | l.lawrence@erems.net | 118.119.20.150 | Full-time | Admin | 12:27:19 pm (0 minutes ago) | 10/1/2019 | N/A |
| Jesse Pena | Graphic designer | j.pena@erems.net | 186.125.232.66 | Part-time | Admin | 4:55:05 pm (1 day ago) | 11/16/2020 | N/A |
| Catherine Martin | Sales associate | catherine_M@erems.net | 247.168.184.57 | Full-time | Admin | 12:17:34 am (10 minutes ago) | 10/1/2019 | N/A |
| Jyoti Patil | Account manager | j.patil@erems.net | 159.250.146.63 | Full-time | Admin | 10:03:08 am (2 hours ago) | 10/1/2019 | N/A |
| Joanne Phelps | Sales associate | j_phelps123@erems.net | 249.57.94.27 | Seasonal | Admin | 1:24:57 pm (2 years ago) | 11/16/2020 | 1/31/2020 |
| Ariel Olson | Owner | a.olson@erems.net | 19.7.235.151 | Full-time | Admin | 12:24:41 pm (4 minutes ago) | 8/1/2019 | N/A |
| Robert Taylor Jr. | Legal attorney | rt.jr@erems.net | 152.207.255.255 | Contractor | Admin | 8:29:57 am (5 days ago) | 9/4/2019 | 12/27/2019 |
| Amanda Pearson | Manufacturer | amandap987@erems.net | 101.225.113.171 | Contractor | Admin | 6:24:19 pm (3 months ago) | 8/5/2019 | N/A |
| George Harris | Security analyst | georgeharris@erems.net | 70.188.129.105 | Full-time | Admin | 05:05:22 pm (1 day ago) | 1/24/2022 | N/A |
| Lei Chu | Marketing | lei.chu@erems.net | 53.49.27.117 | Part-time | Admin | 3:05:00 pm (2 days ago) | 11/16/2020 | 1/31/2020 |

### Event Log (Provided Entry)
- **Event Type:** Information
- **Event Source:** AdsmEmployeeService
- **Event ID:** 1227
- **Date:** 10/03/2023
- **Time:** 8:29:57 AM
- **User:** Legal\Administrator
- **Computer:** Up2-NoGud
- **IP:** 152.207.255.255
- **Description:** Payroll event added. FAUX_BANK
