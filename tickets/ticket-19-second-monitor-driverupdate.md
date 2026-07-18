# Ticket 19 — Second Monitor Not Detected (Flickering, No Signal)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | Medium (workspace reduced during month-end close) |
| Category | Hardware / Software (display driver) |
| Reported symptom | Second monitor shows "No Signal" with intermittent flickering. Monitor powers on but the PC does not appear to detect it. Worked the previous day. |

---

## 1. Diagnosis

The user had already ruled out several causes before the ticket was picked up:

- Swapped the cable — no change.
- Tried a different video port on the PC — no change.
- Tested the monitor on a coworker's laptop — the monitor worked there.

With the monitor confirmed functional on another machine, and the failure
following this specific PC across multiple ports and cables, the fault is not the
monitor, the cable, or one bad port. A failure that follows the PC itself across
different physical connections points to the video output at the software level —
the graphics driver.

The reported flickering supports this: an intermittent signal (briefly present,
then lost, repeating) is consistent with the driver enumerating the display
unreliably, rather than a constant "nothing detected" state. Display Settings was
considered as a first, low-cost check (using "Detect" to see if Windows would
recognise an already-connected display), but this option was not available in the
environment — consistent with Windows having no stable display to detect between
flicker states.

## 2. Root cause

The graphics driver was not reliably recognising the second display output.

## 3. Action taken

- Connected to the user's PC via Remote Support.
- Opened System Update and checked for updates; a graphics driver update was
  available.
- Installed all available updates, including the graphics driver.
- Restarted the PC as prompted.

## 4. Verification

- Second monitor detected and displaying correctly after the restart.
- User confirmed both monitors were working normally.

## 5. Status

**Resolved** — graphics driver updated; second monitor detected and stable.

---

## Lessons learned

1. **A fault that follows the PC across multiple cables, ports, and a
   known-working monitor points to the driver, not the hardware.** The user's own
   troubleshooting (different cable, different port, monitor tested elsewhere) had
   already eliminated the physical layer before the ticket was picked up.

2. **Flickering versus a flat, constant failure is a diagnostic clue.** Intermittent
   signal loss suggests an unstable driver-level handshake rather than a complete
   absence of detection, and points toward a driver fix rather than a settings or
   cabling issue.

3. **Cheap checks first, but let the evidence lead.** Checking Display Settings for
   a "Detect" option is a reasonable low-cost first step, but when the user's prior
   troubleshooting already isolates the fault to the PC itself across multiple
   connections, that evidence should carry more weight than a generic first
   instinct.
