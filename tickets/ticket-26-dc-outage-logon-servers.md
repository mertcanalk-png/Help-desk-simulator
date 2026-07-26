# Ticket 26 — "No Logon Servers Available" (Domain Controller Outage)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | Critical (approximately 40 users unable to start their workday) |
| Category | Network / Infrastructure — Identity |
| Reported symptom | Most of the office cannot log in, with the error "no logon servers available." A small number of users can still log in normally, and some already-logged-in users cannot reach network resources. |

---

## 1. Diagnosis

The scale of impact (most of the office) combined with a small number of
unaffected users pointed toward the domain controllers rather than individual
machines. With two domain controllers in the environment, clients can authenticate
against either one depending on which is located for them — if one DC is down,
users whose client would normally reach that DC fail, while users who happen to
reach the other DC continue to log in normally. That pattern is consistent with a
single domain controller being unavailable rather than a full domain-wide failure.

DC01 and DC02 were checked in the server room. DC01 showed a status of
offline/unresponsive. DC02 was checked and confirmed healthy.

## 2. Root cause

DC01 was offline, removing authentication for any client relying on it, while
DC02 remained available and continued to serve the users directed to it —
accounting for the small number who could still log in.

Note: the reason DC01 went offline was not established.

## 3. Action taken

- Isolated the issue to the domain controllers based on the scale and pattern of
  impact.
- Checked both DC01 and DC02; confirmed DC01 offline and DC02 healthy.
- Rebooted DC01.
- Confirmed DC01 returned to an online state.
- Confirmed with the reporting user that login was restored.

## 4. Verification

- DC01 online after reboot.
- User confirmed successful login.

## 5. Status

**Resolved (cause of DC01 outage unconfirmed; post-recovery replication not
checked)** — logon restored following the DC01 reboot.

---

## Lessons learned

1. **With multiple domain controllers, a partial-impact pattern is itself
   diagnostic evidence.** Some users still logging in while most cannot is
   consistent with one DC being down and another still serving a subset of
   clients, rather than a contradiction to explain away.

2. **Confirm the health of all domain controllers, not just the one that is
   obviously down.** Checking DC02 confirmed it was carrying the authentication
   load safely, rather than assuming it was fine.

3. **After a domain controller recovers from an outage, replication with other
   domain controllers should be verified**, not just that the DC itself is back
   online. A recovering DC needs to catch up on any changes made elsewhere while it
   was unavailable; unchecked replication can leave the two DCs' data inconsistent
   in ways that surface as unrelated problems later. This step was not performed
   here and is noted as a follow-up for a production environment.
