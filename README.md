# Entra PIM and Access Reviews Lab

> **Loom walkthrough:** _link coming soon_

Lab 7 of the Lakeview Health series. Nobody keeps admin rights permanently, and nobody keeps access that no one vouches for. A Junior Developer can elevate to Contributor for one hour with MFA and a reason, and a group access review removes anyone the reviewer denies.

## What this proves

| Skill | Evidence |
| --- | --- |
| Just in time access | Contributor eligible (not active) in PIM, scoped to one resource group |
| Elevation controls | 1 hour max, justification and MFA required |
| Audit trail | PIM resource audit shows who elevated, when and why |
| Access reviews | Group review with auto apply; the denied user was removed |
| Compliance evidence | Redacted review results and PIM audit in [`evidence/`](evidence) |

## Results

| Test | Expected | Result |
| --- | --- | --- |
| Jordan activates Contributor | Needs MFA and a reason, expires in 1 hour | _pending_ |
| Activation logged | Shows in Resource audit | _pending_ |
| Access review deny | User removed from group automatically | _pending_ |

## Production notes

- Require approval from a second admin for high impact roles (Owner, User Access Administrator, Global Administrator).
- Run reviews quarterly and send reminders; unreviewed access is removed.
- Review PIM eligible assignments too, not just group members.

Run it: [LAB-GUIDE.md](LAB-GUIDE.md).
