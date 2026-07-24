# Ticket 22 — Both Desk Monitors Black When Docked (Daisy-Chain Cable)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | Medium (down to a single laptop screen, spreadsheet work impaired) |
| Category | Hardware — Peripherals |
| Reported symptom | Both desk monitors go black when the laptop is docked; the laptop's own screen works normally. Previously worked with no changes made by the user. |

---

## 1. Diagnosis

The laptop's own screen working normally while both external monitors failed
together pointed away from the laptop or dock itself and toward the monitor
connection path. The two monitors were connected in a **daisy chain** — one cable
from the dock to the first monitor, then a second cable from the first monitor to
the second.

In this topology, the second monitor's signal passes through the first monitor's
connection. A failure at the first link (dock to Monitor 1) removes the signal to
both displays, even if the cable between Monitor 1 and Monitor 2 is functioning
normally. This explains both monitors going dark together without requiring a
fault on each individual cable.

Basic troubleshooting had already been attempted without success: re-docking
several times, unplugging and reseating the video cables, and restarting the
computer.

## 2. Root cause

A fault in the first cable of the daisy chain (dock to Monitor 1) is the most
consistent explanation for both monitors losing signal simultaneously, given the
chain topology and the laptop's own display remaining unaffected.

Note: the user was asked to send a photo of the cable to confirm its type (HDMI),
so the correct replacement part could be ordered. The photo confirmed cable type
only — it did not show visible physical damage, and no damage was independently
confirmed. The diagnosis rests on the daisy-chain topology and the failure of
reseating/restart to resolve the issue, not on visual confirmation of a faulty
cable.

## 3. Action taken

- Directed the user through cable reseating and a restart, without a non-technical
  user having to identify cable types unaided.
- Had the user photograph the cable to confirm its type ahead of ordering a
  replacement.
- Arranged a replacement HDMI cable through Ship Manager with rush priority, given
  the user was fully down to a single small screen.

## 4. Verification

- User confirmed both external monitors came on and worked normally once the
  replacement cable was installed.

## 5. Status

**Resolved** — replacement cable restored both external monitors.

---

## Lessons learned

1. **Understand the physical topology before diagnosing a multi-device failure.**
   Daisy-chained displays share a single point of failure at the first link; that
   detail is what makes "one bad cable, two dead monitors" a coherent diagnosis
   rather than a coincidence.

2. **A photo can confirm cable type without confirming a fault.** Remote diagnosis
   with a non-technical user has real evidence limits — using a photo to identify
   the correct replacement part is legitimate, but it should not be written up as
   visual confirmation of damage unless damage was actually visible.

3. **Physically replacing hardware is a bigger commitment than a software fix and
   should be reasoned accordingly.** With no way to test the cable further given the
   user's technical comfort level and remote setup, replacement based on topology
   and process of elimination was a reasonable call — but the reasoning behind that
   call belongs in the notes, not an assumed fault.
