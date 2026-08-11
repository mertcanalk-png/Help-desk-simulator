# Ticket 34 — New USB Headset, No Sound (Missing Driver on Corporate Image)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | Medium |
| Category | Hardware / Software (driver) |
| Reported symptom | New wired USB headset produces no sound at all — complete silence, no buzzing or background noise. Different USB ports tried with no change. Headset also tested on other computers with no sound. |

---

## 1. Diagnosis

The headset had already been tested on other computers with the same result,
which at first appears to rule out a single-machine driver issue — a driver
problem is normally specific to one computer's configuration. However, the other
computers tested were also corporate machines built from the same standard image.
Testing the headset on machines that share an identical software baseline is not
an independent test: if the required driver is missing from that shared image,
every machine built from it would show the same failure, including the ones
already tried. The multi-computer failure is therefore consistent with a driver
gap at the corporate image level, not evidence against a driver cause.

## 2. Root cause

The driver required for this headset model was not present on the standard
corporate image, so the headset produced no sound on any machine using that image,
including the ones already tested.

## 3. Action taken

- Connected to the user's machine via remote support.
- Downloaded and installed the correct driver from the official vendor.
- Restarted the computer.

## 4. Verification

- User confirmed sound was working after the restart.

## 5. Status

**Resolved** — correct driver installed; sound confirmed working.

---

## Lessons learned

1. **A test only rules something out if it is genuinely independent.** Testing a
   device on other machines that share the same software image is not an
   independent test of the device itself — it can reproduce the same gap rather
   than ruling it out.

2. **"Fails on multiple computers" does not always mean the device is at fault.**
   On a fleet of identically imaged machines, a missing driver produces exactly
   this pattern; the shared configuration, not the individual devices, is worth
   checking first.

3. **A driver gap found for one user likely affects others with the same
   hardware.** Since the driver is missing from the standard image, any other
   employee issued this same headset model will hit the identical fault —
   worth flagging to the imaging/endpoint team to add the driver to the base image
   and prevent repeat tickets.
