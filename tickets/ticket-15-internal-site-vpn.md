# Ticket 15 — Remote User Cannot Reach Internal HR Portal

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | Medium (PTO approvals blocked; team waiting) |
| Category | Network / Access |
| Reported symptom | Remote user gets "This site can't be reached" for the internal HR portal (`hr.corp.local`). Regular websites load fine; a different browser made no difference. |

---

## 1. Diagnosis

Two details isolated the fault immediately:

- The unreachable address is an **internal-only name** (`.corp.local`) — a name
  that exists only in the company's internal DNS, not on the public internet.
- Everything internet-facing works normally.

Internal resources failing while the public internet works is the signature of a
user who is not on the corporate network. For a remote user, that means the VPN
tunnel. (Same underlying pattern as Ticket 02, where the symptom surfaced as a file
share error rather than a browser error.)

Connected via remote support and checked the VPN client: the tunnel was not
active.

## 2. Root cause

The VPN tunnel was not active, so the machine had no path to the corporate
network — and no access to internal DNS, meaning `hr.corp.local` could not even
resolve. Off-VPN, the failure occurs at name resolution: public DNS has no record
for internal-only names, which is why the browser reports the site as unreachable.

Note: whether the tunnel had dropped during the session or was never started that
day was not determined.

## 3. Action taken

- Connected to the user's machine via remote support.
- Confirmed the VPN tunnel was inactive.
- Restored the VPN connection.
- Verified `hr.corp.local` was reachable before handing back to the user.

## 4. Verification

- Portal confirmed reachable after the tunnel was restored.
- User confirmed access to the HR platform and pending approvals.

## 5. Status

**Resolved** — VPN tunnel restored; internal portal reachable and confirmed by the
user.

---

## Lessons learned

1. **Internal-only failure + working internet = not on the corporate network.**
   For a remote user, check the VPN tunnel before anything else. The same root
   pattern presents through different symptoms — a file-share error in one ticket,
   a browser error here.

2. **Internal DNS names only resolve on the corporate network.** A `.local`-style
   address has no public DNS record; off-VPN the name cannot resolve at all, which
   explains the browser error. Understanding where the failure occurs (resolution,
   not the server) makes the diagnosis precise.

3. **Verify before handing back.** Confirming the resource is reachable from the
   user's machine before asking them to retry closes the loop on the fix rather
   than assuming it.
