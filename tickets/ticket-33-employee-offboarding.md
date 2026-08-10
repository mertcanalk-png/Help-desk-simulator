# Ticket 33 — Employee Offboarding (Account Deprovisioning)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | Medium (security compliance requirement, deadline end of business Friday) |
| Type | Service Request — offboarding |
| Category | Identity / Access |
| Request | Deprovision a departing employee's account per the offboarding checklist: disable, reset password, remove licenses, remove group memberships, recover company device. HR-approved, manager notified, last day Friday. |

---

## 1. Verification before action

This is a third-party request — HR requesting action on another employee's
account, not the account owner contacting support directly. Before making any
change, the account found in the directory was cross-checked against the reported
details (department, employee identification) to confirm it was the correct
individual, rather than acting on a name match alone. Offboarding the wrong
account would leave an active employee locked out in error.

Timing was also treated as part of the request: the action was carried out on the
stated last day (Friday) rather than as soon as the ticket arrived, so the
employee's access was not cut prematurely while she was still working, and access
did not remain open past her departure.

## 2. Action taken

- Located and confirmed the correct account in the directory.
- Disabled the account (retained, not deleted, per standard offboarding practice).
- Reset the password.
- Removed all assigned licenses.
- Removed all group memberships except the default Domain Users group.
- Located the employee's assigned device in Asset Management and processed its
  return with a return label.

## 3. Verification

- Confirmed the account showed as disabled with licenses and group memberships
  removed.
- Confirmed the device was logged for return in Asset Management.

## 4. Status

**Resolved (request fulfilled)** — account deprovisioned per the offboarding
checklist, timed to the employee's last day; device return in progress.

---

## Lessons learned

1. **Verify the target account for a third-party request, not just the name.**
   Offboarding is a request made about someone else's account; confirming the
   match against department or employee ID before acting avoids disabling the
   wrong person.

2. **Timing is part of correctly fulfilling an offboarding request.** Carrying out
   deprovisioning on the stated last day, rather than immediately on receipt,
   avoids prematurely cutting off a still-active employee while still meeting the
   compliance deadline.

3. **Disable, don't delete.** Retaining a disabled account preserves the ability to
   review or restore access if needed, rather than an irreversible deletion.
