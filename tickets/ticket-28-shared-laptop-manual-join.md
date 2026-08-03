# Ticket 28 — Shared Warehouse Laptop Dead, Manual Domain Enrollment Replacement

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | High (whole floor blocked; stock counts due same day) |
| Category | Hardware — Shared/Domain-Enrolled Device |
| Reported symptom | Shared warehouse inventory-scanning laptop will not power on — no lights, no fan. A second charger and a known-good outlet were already tried with no change. |

---

## 1. Diagnosis

No lights and no fan on a confirmed known-good outlet, with a second charger
already tried, rules out a bad outlet or charger and confirms the unit itself has
failed. This follows the same confirm-before-condemning approach as a standard dead
desktop (known-good power source ruled in before declaring hardware failure).

The device required a different replacement path than a typical single-user
machine: it is a shared, domain-enrolled laptop that everyone on the floor signs
into for scanning, not a per-user cloud-managed device. Shared domain-enrolled
machines like this are built by hand and joined directly to the domain, rather
than provisioned through Cloud Identity/Device Manager — this applies regardless
of the device being a laptop.

## 2. Root cause

Hardware failure of the shared laptop, confirmed dead on a known-good outlet and a
second charger.

## 3. Action taken

- Confirmed the failure via Team Chat with the Facilities lead (known-good outlet,
  second charger, still dead).
- Selected a laptop as the replacement device type (Ship Manager enforces matching
  device types).
- Built the replacement in Computer Deployment using manual domain enrollment:
  created the local administrator account at first setup, renamed the machine to
  **SD0100** (the next free number confirmed against the asset register, following
  the site's SD#### naming convention), joined it to the domain, and confirmed
  domain sign-in.
- Installed all four baseline applications (VPN Client, Team Chat, Mail Client,
  System Update) using the official vendor download link for each, avoiding
  sponsored search results as required for manually built machines.
- Registered the new laptop in Asset Management and set its status to Ready.
- Checked the replacement out to the **Onsite Warehouse**, not to the individual
  reporting user, since this is shared site equipment.
- Obtained the site receiving dock address from the Facilities lead and shipped the
  configured laptop there via Ship Manager with Rush Priority (same day) and an
  included return label.
- On confirmation from the Facilities lead that the replacement arrived, requested
  the dead unit be returned using the prepaid label.

## 4. Verification

- Replacement laptop confirmed built, domain-joined, and running all baseline
  applications before shipping.
- Facilities lead confirmed arrival of the replacement before the dead unit's
  return was requested.

## 5. Status

**Resolved** — shared laptop replaced via manual domain enrollment; dead unit
recovery initiated after confirmed delivery.

---

## Lessons learned

1. **Shared, domain-enrolled devices follow a different provisioning path than
   personal machines**, even when the device type (laptop) would otherwise suggest
   cloud enrollment. The deciding factor is how the device is used — shared sign-in
   — not its form factor.

2. **Shared equipment ships to the work site, not an individual's address.**
   Asset check-out and shipping destination both follow the equipment, not the
   person who happened to report the fault.

3. **Follow naming and download conventions exactly, not just approximately.**
   Confirming the next free SD#### against the register, and using only official
   vendor links instead of sponsored results, both prevent asset-register
   conflicts and reduce exposure to malicious download sources.

4. **Sequence the return around confirmed delivery.** Requesting the dead unit's
   return only after the replacement is confirmed received avoids a gap where the
   site has neither a working nor a spare unit.
