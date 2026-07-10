# Ticket 08 — New Hire Access Setup (Provisioning)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | High (access required for Monday 9 AM orientation) |
| Type | Service Request — new hire provisioning |
| Category | Identity / Access |
| Request | Create a Directory account for a new Engineering starter and provision group access. |

---

## 1. Request detail

New-hire access setup for a Junior Developer in Engineering, submitted by HR.
Account and access required before orientation.

Requested provisioning:
- New Directory account (`jtorres`, Engineering department)
- Membership of three groups: **Engineering**, **VPN-Users**, **CodeRepo-Access**

## 2. Verification before action

The request was submitted by a person sharing the same surname as the new starter.
Before creating anything, the target account was confirmed to be the new employee
(`jtorres`), distinct from the requester, so that the account was created for the
correct person rather than a similarly named existing user.

## 3. Action taken

- Created the account `jtorres` in the Engineering OU using the details supplied.
- Set **"user must change password at next logon"** so the starter sets their own
  password on first sign-in and the technician never holds it.
- Added the account to the three requested groups: Engineering, VPN-Users, and
  CodeRepo-Access.

## 4. Verification

- Confirmed the account exists and is enabled.
- Confirmed all three group memberships are present.
- Account is ready for first logon ahead of the orientation deadline.

## 5. Status

**Resolved (request fulfilled)** — account created, access provisioned and verified.

---

## Lessons learned

1. **Verify identity by unique account, not by name.** When a request involves
   people who share a surname (here the requester and the new starter), confirm the
   exact target account before acting to avoid modifying the wrong user.

2. **Provisioning is a request, not an incident.** There is no root cause to
   investigate; the measure of success is that the account and access match the
   request and are confirmed working. Documentation reflects fulfilment, not
   diagnosis.

3. **Set force-password-change on new accounts.** The starter sets their own
   password at first logon, so the credential is never known to the technician —
   standard practice for account creation.

4. **Confirm the provisioning rather than assuming it applied.** Access tied to a
   fixed start deadline is only complete once the account state and group
   memberships have been checked, not just submitted.
