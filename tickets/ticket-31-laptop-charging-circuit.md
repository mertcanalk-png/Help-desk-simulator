# Ticket 31 — Laptop Won't Charge (Charging Circuit, Not the Charger)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | High (laptop losing power, productivity at risk) |
| Category | Hardware |
| Reported symptom | Laptop will not charge. Multiple outlets tried. Charger light flickers, battery stuck at a low percentage. User suspected the charger was faulty. |

---

## 1. Diagnosis

The reported symptom — a flickering charger light — does not by itself distinguish
between a faulty charger and a poor connection at the laptop's own charging port;
both can produce the same flickering behaviour. The user's own theory (a bad
charger) was a reasonable guess but not something to act on directly, since
replacing the whole device on a guess would be a costly escalation if the charger
was not actually the problem.

The correct approach was to test the cheaper, faster explanation first: swap in a
confirmed-good charger and see whether the fault follows the charger or stays with
the laptop.

## 2. Root cause

The laptop's own charging circuit, not the charger. This was established by
elimination: a new charger was supplied and the laptop still would not charge,
which rules out the charger and implicates the laptop itself.

## 3. Action taken

- Confirmed the reported issue and obtained the user's shipping address.
- Shipped a replacement charger as the low-cost first test.
- Confirmed with the user that the laptop still would not charge with the new
  charger — ruling out the charger.
- Escalated to a full device replacement, first confirming the affected device
  was a laptop (to avoid shipping the wrong device type).
- Built the replacement laptop.
- Shipped the replacement laptop with a prepaid return label and rush priority.
- On confirmation the replacement arrived, had the user return the faulty unit
  using the prepaid label.

## 4. Verification

- User confirmed the new charger did not resolve the issue, confirming the fault
  was in the laptop.
- User confirmed the replacement laptop was charging and working normally.

## 5. Status

**Resolved** — faulty laptop identified by elimination and replaced; original unit
recovered.

---

## Lessons learned

1. **Always test the cheap fix first, even if the user's own theory might be
   wrong.** Sending a replacement charger before committing to a full device
   replacement cost little and quickly ruled the charger in or out — the same
   principle holds even though it turned out not to be the cause.

2. **An ambiguous symptom can point to more than one component.** A flickering
   charge light does not distinguish a bad charger from a bad connection at the
   laptop's charging port; only swapping in a known-good component actually
   isolates which side is at fault.

3. **Confirm device type before shipping a replacement.** Shipping the wrong
   device type (desktop instead of laptop, or vice versa) is a costly and avoidable
   mistake — confirming first is a small step that prevents a large one.

4. **Sequence the return around confirmed delivery of the replacement**, so the
   user is never left with neither a working unit nor a spare.
