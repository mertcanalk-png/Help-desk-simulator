# Ticket 38 — CRM Repeatedly Crashing (Business-Critical, Time-Sensitive)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | High (active deal in progress, escalation threatened within 10 minutes) |
| Category | Software |
| Reported symptom | Voicemail report: CRM application crashing repeatedly, already restarted three times with no change, while an active deal was in progress. |

---

## 1. Diagnosis

The crash was generic, with no network- or connectivity-related error accompanying
it. Troubleshooting began with the network connection (checking the Ethernet
cable, then testing over WiFi as a separate connection path) before moving to the
application itself. Since the crash was not accompanied by any evidence pointing
at connectivity, this was a systematic starting point rather than one the symptom
itself indicated, and added time under a situation with an explicit, very short
deadline.

The application persisted in crashing on both Ethernet and WiFi, ruling out the
network as a factor. Investigation then moved to the application: a repair of the
application (a general reset of its files/configuration) was attempted first and
did not resolve the crashing. Clearing the application's cache was attempted next
and resolved it.

Before clearing the cache — an action that can remove unsaved local session data —
the user's deal data was confirmed to be saved/synced, given the live, high-value
transaction in progress.

## 2. Root cause

A corrupted application cache, confirmed by the general repair step failing to
resolve the crash while the more targeted cache clear did.

## 3. Action taken

- Connected to the user's machine via remote support.
- Checked the Ethernet connection and cable; no fault found.
- Tested over WiFi as a separate connection path; crashing persisted.
- Ran the application's repair function; crashing continued.
- Confirmed the user's deal data was saved before proceeding.
- Cleared the application's cache.

## 4. Verification

- Application ran without crashing after the cache was cleared.
- User confirmed the CRM was stable and usable.

## 5. Status

**Resolved** — corrupted application cache cleared; crashing stopped.

---

## Lessons learned

1. **Let the evidence, not a default checklist, decide where to start under time
   pressure.** With a generic crash and no connectivity error, the application was
   the more probable cause from the outset; ruling out the network first cost time
   that mattered given the explicit short deadline.

2. **Escalate from general to targeted fixes, and note which one actually
   worked.** The application repair did not resolve the issue; the cache clear
   did. Recording both, and which one succeeded, keeps the diagnosis precise
   rather than crediting the wrong action.

3. **Check for unsaved work before a data-risking action, especially on a live,
   high-value task.** Confirming the deal data was saved before clearing the cache
   avoided turning a software crash into a data-loss incident on an active
   business-critical transaction.

4. **Stay methodical under escalation pressure.** A tight deadline and a threat to
   escalate did not change the approach — each step was still verified before
   moving to the next, rather than skipping checks to save time at the risk of the
   user's data.
