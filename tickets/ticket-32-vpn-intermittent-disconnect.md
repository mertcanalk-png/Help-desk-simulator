# Ticket 32 — VPN Repeatedly Disconnecting (Remote Worker)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | Medium |
| Category | Network / Access |
| Reported symptom | Remote user's VPN connects successfully, then disconnects on its own after some time and will not stay connected. General web browsing at home works normally; only company-internal access via VPN is affected. |

---

## 1. Diagnosis

General web browsing was confirmed fully reliable throughout, with only the VPN
tunnel repeatedly disconnecting. This detail does not support a general ISP
outage or degraded connection — a broad ISP-level problem would typically affect
ordinary browsing as well, not the VPN exclusively. A fully stable general
connection alongside a specifically failing VPN tunnel points more toward a
VPN-specific cause: the VPN client itself, the home router's handling of that VPN
protocol over a longer session, or a session/timeout setting on the VPN server
side.

Two troubleshooting steps were performed but do not conclusively rule out the
home network:

- The modem was power-cycled with an approximately 3-second unplug. This is
  shorter than the approximately 30 seconds typically needed for a full reset,
  so it may not have fully cleared any router-side state.
- The VPN was not tested on a separate network (for example, a mobile hotspot),
  which would have definitively distinguished a home ISP/router cause from a
  VPN client or server-side cause.

## 2. Root cause

Not conclusively established. The evidence gathered (fully reliable general
browsing, VPN specifically dropping) points away from the ISP explanation given
to the user, but no test was performed that isolates the VPN client, the home
router's handling of the VPN protocol, or the VPN server as the specific cause.

## 3. Action taken

- Had the user power-cycle the modem (brief unplug) and restart the PC; the VPN
  still failed to connect afterward.
- Advised the user to contact their ISP.

## 4. Verification

Not completed — the user was directed to their ISP without confirmation that the
ISP is the actual cause, and without a follow-up test to confirm the VPN issue is
resolved.

## 5. Status

**Escalated to user's ISP (cause not conclusively isolated)** — the evidence
gathered (reliable general browsing) does not strongly support the ISP
explanation given; a stronger isolation test was not performed before concluding
the cause.

---

## Lessons learned

1. **Weigh evidence against the conclusion before handing it off.** Fully reliable
   general browsing alongside a VPN-only failure does not point at a general ISP
   problem; the diagnosis should follow what the gathered evidence actually shows,
   not default to the most familiar explanation.

2. **A modem power cycle needs a full reset duration to be a valid test.**
   A few seconds is unlikely to fully clear the device's state; roughly 30 seconds
   is the standard guidance, and a too-short cycle can produce a false "still
   broken" result.

3. **Test on a different network to isolate ISP/router from VPN client or server.**
   Trying the VPN over a mobile hotspot would have directly separated a home
   network cause from a VPN-specific cause, rather than concluding from an
   incomplete test.

4. **Sending a user to contact their ISP on an unconfirmed cause has a real cost.**
   If the ISP finds nothing wrong, the user has lost time and the underlying issue
   remains — the diagnosis should be as conclusive as reasonably possible before
   escalating outside the organisation.
