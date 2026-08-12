# Ticket 36 — Laptop Charger Not Working (Isolated by Swap Test)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | Medium |
| Category | Hardware |
| Reported symptom | Laptop charger does not work. Reported via phone call. |

---

## 1. Diagnosis

A structured elimination test was used rather than assuming a cause:

- Tried a different wall outlet — no change, ruling out the outlet.
- Tried a known-good charger (a colleague's) on the same laptop — charging worked.

Holding the laptop and outlet constant while swapping only the charger, and having
the laptop charge successfully with the substitute, isolates the fault to the
original charger rather than the laptop's charging circuit or the power source.
This is the mirror case of a laptop-side charging circuit fault, where a
known-good charger still fails to charge the machine — here the opposite result
confirms the fault sits with the charger itself.

## 2. Root cause

The original charger was damaged, confirmed by a known-good charger resolving
charging on the same laptop and outlet.

## 3. Action taken

- Guided the user through the outlet and known-good-charger swap tests by phone.
- Ordered a replacement charger via Ship Manager with rush priority.

## 4. Verification

- User confirmed the replacement charger arrived and charging worked normally.

## 5. Status

**Resolved** — original charger confirmed faulty by elimination; replacement
charger resolved the issue.

---

## Lessons learned

1. **A known-good component swap on the same machine is a clean, decisive test.**
   Holding the laptop and outlet constant and changing only the charger gives an
   unambiguous result, rather than guessing which part is at fault.

2. **Document the reasoning behind the diagnosis, not just the conclusion.** Noting
   that a substitute charger resolved charging on the same laptop and outlet gives
   the next reader the evidence, not just a stated belief.

3. **Confirm whether expedited shipping is actually justified before defaulting to
   it.** Asking whether the user has an interim way to charge (a spare charger, a
   dock) helps determine whether rush priority is necessary, rather than applying
   it by default regardless of business impact.
