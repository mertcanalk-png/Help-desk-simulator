# Ticket 29 — Full-Screen Scareware Warning

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | High (user locked out of the desktop, under pressure to call a fake support number) |
| Category | Security / Social Engineering |
| Reported symptom | Full-screen red warning claiming the computer is infected, with a loud alarm and a countdown, pressuring the user to call a phone number immediately. The warning fills the entire screen with no visible way to close it. User had not called the number. |

---

## 1. Diagnosis

The combination of a full-screen takeover, an alarm sound, a countdown, and
pressure to call a phone number is the signature of scareware: a web page
designed to imitate a system-level infection alert and panic the user into
calling a fake support line. It is not an actual infection — it is a browser page
using urgency and visual takeover to manipulate the user, with the real risk being
what happens if the number is called (a scammer posing as support, typically
seeking remote access or payment), not the page itself.

The user had already done the most important thing correctly: not calling the
number.

## 2. Action taken

- Reassured the user not to call the number.
- Connected via Remote Support.
- Located the page's hidden close control by moving the mouse to the top-left
  corner of the warning (scareware pages commonly hide their close button to keep
  the user trapped on the page) and closed it.
- Ran a full security scan to confirm nothing had been installed alongside the
  scareware page.

## 3. Root cause

A scareware web page designed to simulate a system infection and pressure the user
into calling a fraudulent support number.

## 4. Verification

- Full security scan completed and returned clean, confirming no additional
  payload was present.
- Desktop confirmed back to normal.

## 5. Status

**Resolved** — scareware page closed, no infection found, desktop restored to
normal.

---

## Lessons learned

1. **Scareware is a social-engineering page, not necessarily an actual
   infection.** The full-screen takeover, alarm, and countdown are designed to
   provoke a panicked phone call — the real danger is the user calling the number,
   not the page itself.

2. **Scareware pages commonly hide their close control** to trap the user on the
   page; checking corners and edges of the screen for a hidden close button is a
   simple, low-risk first step before assuming a forced restart is needed.

3. **Run a scan after closing the page, even when it is expected to be "just a
   browser page."** Confirming a clean result rules out the possibility of an
   additional payload having been delivered alongside the scareware, rather than
   assuming it based on the page's apparent nature.

4. **The user not calling the number was the critical correct action.** No
   technical fix undoes the damage of a user handing control to a scammer over the
   phone; reinforcing "never call the number" is as important as the technical
   remediation itself.
