# Ticket 21 — Cafeteria Printer Offline (Stale IP Address)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | Medium (daily cafeteria menus and event materials blocked) |
| Category | Hardware / Network — Print Services |
| Reported symptom | Cafeteria network printer shows offline on the reporting computer despite being powered on with paper loaded. Was working a couple of weeks earlier. |

---

## 1. Diagnosis

The printer was confirmed powered on with paper present, so the fault was in the
connection between the computer and the device rather than the printer itself.
Driver updates were checked and found current, which rules out an outdated driver
but does not address the connection layer.

The printer entry was removed and re-added using the printer's IP address from
network documentation. The address used to re-add the printer differed from the
one the existing queue entry had been configured with — the printer's IP address
had changed since the queue was originally set up, and the computer's print queue
was still pointing at the old, now-incorrect address. This is why the device
showed as offline despite being powered on and reachable at its current address.

## 2. Root cause

The printer's IP address had changed, and the previously configured print queue
entry still referenced the old address, so the computer could not reach the
device.

## 3. Action taken

- Confirmed driver updates were current (ruled out, not the cause).
- Removed the existing printer entry.
- Re-added the printer using its current IP address (10.0.2.54) sourced from
  network documentation.
- Sent a test print to confirm functionality.

## 4. Verification

- Printer showed online immediately after re-adding with the current address.
- Test page printed successfully.

## 5. Status

**Resolved** — print queue reconfigured with the printer's current IP address;
printing confirmed working.

---

## Lessons learned

1. **"Offline" on a network device often means a stale address, not a driver
   fault.** Checking for driver updates was a reasonable first step but addressed
   the wrong layer — the issue was the queue's configured address no longer
   matching the device, not the driver itself.

2. **A device that "was fine a couple of weeks ago" and then went offline suggests
   something changed, not something broke.** An IP address change is a common cause
   of exactly this pattern, and is worth checking before assuming hardware or
   driver failure.

3. **Shared network devices should use a static IP or a DHCP reservation.** If this
   printer is on a standard DHCP lease, its address can change again and cause the
   same fault to recur. Recommending a fixed address for shared infrastructure like
   printers prevents this class of ticket from repeating.
