# Ticket 07 — All Printers Offline, Building-Wide

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | High (business-critical — whole-company outage) |
| Category | Infrastructure / Print Services |
| Reported symptom | Every printer in the building shows offline. Jobs sent from multiple floors, nothing prints anywhere. Worked the previous evening. |

---

## 1. Diagnosis

The issue was reported as a printer fault. The deciding factor was the scope rather
than the reported cause:

- Every printer, on every floor, offline at the same time.
- Jobs from multiple floors all fail.
- The service worked the previous evening.

A large number of independent printers do not fail simultaneously by coincidence.
When every device of one type fails at once, the fault lies in a component they all
share rather than in the endpoints. For networked printers, that shared dependency
is the print server. The problem was therefore isolated to the print server rather
than any individual printer.

## 2. Root cause

Print services were not running on the print server, so no floor could print.

Note: whether the server itself was fully down or the Print Spooler service on it
had stopped was not separately confirmed, and the reason the service stopped (the
system had worked the previous evening) was not established. The cause of the
outage is therefore unconfirmed.

## 3. Action taken

- Isolated the fault to the print server based on the building-wide scope.
- Rebooted the print server and waited for it to return to service.
- Confirmed the server was active.
- Asked the user to retry printing.

## 4. Verification

- Server confirmed active after reboot.
- User retried and confirmed printing was restored building-wide.

## 5. Status

**Resolved (cause unconfirmed)** — printing restored across the building; the exact
cause of the outage was not isolated.

---

## Lessons learned

1. **Simultaneous multi-site failure indicates a shared dependency, not the
   endpoints.** "All printers, all floors, at once" points to the print server, not
   the printers. Reading the scope of an outage determines where to look before any
   device is touched.

2. **Confirm whole-server-down versus service-hung before rebooting.** If the server
   is running but only the Print Spooler service has stopped, the correct fix is
   restarting that service — faster and with no impact on other work — rather than
   rebooting the whole server, which cancels in-flight jobs and affects anything else
   the server hosts. The fix should match the actual fault.

3. **A working reboot does not confirm the root cause.** With no reason established
   for why the service stopped, the issue can recur. Status is recorded as resolved,
   cause unconfirmed.

4. **A building-wide outage is also a communication event.** Broadcasting a
   known-issue notice prevents duplicate tickets, and the impact of rebooting a shared
   production server during working hours should be weighed before acting.
