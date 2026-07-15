# Ticket 16 — Folder Deleted and Trash Emptied (Cloud Recovery)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | Urgent (months of client proposals and contracts, potential permanent loss) |
| Category | Software / Cloud (data recovery) |
| Reported symptom | User accidentally deleted a folder containing months of client proposals and contracts, then emptied the local Trash. Deletion occurred approximately two hours prior to reporting. |

---

## 1. Diagnosis

Emptying the local Recycle Bin/Trash only clears the local copy. The folder was
synced through a Cloud Drive, which keeps its own deleted-item retention separate
from the local Trash. Files deleted and even locally purged are not necessarily
gone from the cloud service, provided the action falls inside its retention
window. The two-hour gap between deletion and the report was well inside any
standard retention period, making recovery from the cloud side the expected path
rather than a long shot.

## 2. Action taken

- Connected to the user's machine via remote support.
- Opened the Cloud Drive client and forced a sync to pull the current cloud-side
  state.
- Opened **Version History > Recently Deleted Files** (in this client, deleted-item
  recovery is nested inside version history rather than a separate menu) and
  located the deleted folder.
- Restored the folder and its contents.

## 3. Verification

- Restored folder confirmed present with the expected client proposal and contract
  files.
- Opened the recovered proposal file directly and confirmed the content was
  intact, not partial or corrupted.
- User confirmed the recovered files matched what was lost.

## 4. Status

**Resolved** — folder and contents recovered from the cloud service's deleted-item
retention; content verified intact.

---

## Lessons learned

1. **A local Trash/Recycle Bin is not the only copy.** For files synced through a
   cloud service, emptying the local Trash does not remove the cloud-side
   deleted-item retention. Checking the cloud service's own recovery options is a
   standard first step before treating a deletion as permanent.

2. **Retention windows are time-limited — check timing, not just possibility.** A
   two-hour-old deletion is comfortably inside any standard retention window;
   recovery is not guaranteed once that window has passed, so the elapsed time is
   part of the diagnosis.

3. **Confirm content integrity, not just reappearance.** For recovered files headed
   back into active client work, opening the file and checking the content is
   correct is the appropriate verification — a file that has merely reappeared has
   not been confirmed usable.

4. **Know the specific tool's layout.** In this client, deleted-item recovery sits
   inside Version History rather than as a separate feature — verifying the exact
   path in the tool being used avoids wasted time searching the wrong menu.
