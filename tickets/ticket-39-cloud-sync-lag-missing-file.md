# Ticket 39 — Document Missing (Cloud Drive Sync Lag, Not Deleted)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | High |
| Category | Software / Cloud |
| Reported symptom | An important Word document, worked on the previous day, is missing and cannot be found in File Explorer. |

---

## 1. Diagnosis

Before assuming the file was lost, deletion was ruled out first rather than
assumed absent. With deletion excluded, the file's absence from File Explorer
while genuinely still existing pointed toward a sync-lag issue: the Cloud Drive
had not pulled down the latest state, so a file saved correctly was not yet
reflected locally.

## 2. Root cause

The Cloud Drive was out of sync locally; the file had been saved but had not yet
propagated to this device's view in File Explorer. The file was never deleted.

## 3. Action taken

- Connected to the user's machine via remote support.
- Confirmed the file was not in Recently Deleted or otherwise removed.
- Opened the Cloud Drive in File Explorer and forced a sync.

## 4. Verification

- The previously missing file appeared in File Explorer after the sync completed.
- User confirmed the document was accessible.

## 5. Status

**Resolved** — forced sync resolved the local sync lag; file was never deleted.

---

## Lessons learned

1. **"Missing" does not always mean deleted.** A file can be fully intact on the
   server side and simply not yet reflected locally due to sync lag — ruling out
   deletion first avoids treating a sync delay as data loss.

2. **Confirm the cause before applying the fix, even when the fix is quick.**
   Checking that the file was not deleted before forcing a sync meant the
   resulting diagnosis (sync lag) was actually established, not just inferred
   from the fix working.

3. **Sync lag and deletion look similar to the user but need different
   responses.** A missing file understandably alarms a user; distinguishing sync
   lag (a quick, low-risk fix) from genuine deletion (a recovery process) avoids
   unnecessary escalation or unnecessary reassurance in the wrong direction.
