# Ticket 30 — Computer Running Extremely Slow (Multiple Confirmed Causes)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | High (applications taking 5+ minutes to open, freezing, significant productivity impact) |
| Category | Software / Performance |
| Reported symptom | Computer has been extremely slow for several days — applications take minutes to open and the system occasionally freezes. Restarting and closing extra programs did not help. |

---

## 1. Diagnosis

A severe, sustained slowdown of this kind can have more than one contributing
cause, so rather than acting on a single guess, three areas were checked
individually before any fix was applied:

- **Storage** — checked via Settings/Storage.
- **Malware** — checked via a full security scan.
- **Pending updates** — checked via the update tool.

Each check confirmed a real, present issue rather than being fixed on assumption:

- Disk storage was confirmed nearly full.
- The security scan found and removed an actual infection.
- Pending updates were confirmed present and had not been installed.

## 2. Root cause

Three independently confirmed contributing factors: low disk space, an active
infection, and outdated system/driver updates. All three were verified as
genuinely present before being addressed, rather than fixed on the assumption that
they might be involved.

Note: with all three fixed together, the individual contribution of each to the
reported freezing and slow application load times was not isolated separately —
but each was a confirmed, real issue in its own right, not an unproven guess.

## 3. Action taken

- Ran Disk Cleanup to free up nearly-full storage.
- Ran a full security scan, which found and removed an infection.
- Installed all pending system updates.

## 4. Verification

- Confirmed disk space was freed after cleanup.
- Confirmed the scan returned clean after removal.
- Confirmed updates completed successfully.
- User confirmed the computer was running normally, with applications opening at
  expected speed and no further freezing.

## 5. Status

**Resolved** — all three confirmed issues (storage, malware, pending updates)
addressed; performance restored.

---

## Lessons learned

1. **A severe slowdown can have multiple genuine causes at once.** Checking
   storage, malware, and updates as three separate, specific areas — rather than
   guessing at one — surfaced three real, independently confirmed problems rather
   than one.

2. **Confirm each cause before fixing it, even when checking multiple areas.**
   Applying Disk Cleanup, a malware scan, and updates was justified here because
   each check independently confirmed a real issue first — this is different from
   applying multiple fixes on assumption without checking what is actually wrong.

3. **The ticket is resolved once actual causes are fixed, not by running one
   default action.** A single canned fix (for example, only a restart or only an
   update) would have left the other two confirmed problems in place and the
   slowness likely unresolved.
