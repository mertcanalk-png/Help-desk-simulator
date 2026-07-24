# Ticket 23 — Department Drive Letter Missing (VPN + Lost Mapping)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | Medium (critical department files inaccessible for ongoing projects) |
| Category | Network / Access |
| Reported symptom | The department drive letter is no longer listed in This PC at all (not shown as disconnected — simply absent). Was working the previous week. Restarting the computer did not restore it. |

---

## 1. Diagnosis

The reported symptom — the drive letter missing from This PC entirely, rather than
present but showing a broken connection — was checked against two possible causes:
a connectivity issue (no VPN tunnel, as in earlier remote-access tickets) and a
lost drive mapping (the mapping itself no longer configured in Windows).

VPN status was checked first and found disconnected; the VPN connection was
established. The drive was still missing afterward, confirming that connectivity
was not the only factor — the mapping itself had also been lost and required
recreation.

## 2. Root cause

Two contributing issues:

1. The VPN tunnel was not connected, removing the path to the internal file
   server.
2. Independently of the VPN state, the drive mapping itself was no longer present
   in Windows and required remapping — connectivity alone would not have restored
   the drive letter.

## 3. Action taken

- Connected the VPN.
- Confirmed the department (Support) with the user and retrieved the correct UNC
  path from documentation (`\\FILESERV01\departments\Support`).
- Mapped the network drive using the correct drive letter and UNC path.
- Enabled **"Reconnect at sign-in"** so the mapping persists across future logins
  and restarts.

## 4. Verification

- Drive appeared in This PC after remapping.
- User confirmed department files were accessible.

## 5. Status

**Resolved** — VPN restored and drive mapping recreated with persistence enabled.

---

## Lessons learned

1. **Distinguish "unreachable" from "missing" for a network drive.** A drive shown
   with a broken connection points to a connectivity issue (VPN); a drive letter
   absent from This PC entirely points to a lost mapping. These can have different
   causes and are worth telling apart rather than assuming the same fix applies.

2. **Restoring connectivity does not guarantee the mapping still exists.** VPN was
   the first factor checked and fixed, but the drive remained missing afterward —
   confirming a second, independent issue needed its own fix.

3. **Enable "Reconnect at sign-in" when mapping a network drive.** Without it, a
   mapping can fail to persist across a restart or logoff, which is a plausible
   explanation for "it was working last week and is just gone now." Setting it
   addresses recurrence, not just the immediate access.
