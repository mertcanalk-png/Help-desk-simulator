# Ticket 27 — Persistent Pop-Up Ads, Even With Browser Closed

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | High (user unable to work due to constant pop-ups) |
| Category | Security / Software |
| Reported symptom | Screen repeatedly flooded with pop-up ads. Pop-ups continue even when the user is not browsing, and closing them does not stop new ones from appearing. |

---

## 1. Diagnosis

Pop-ups appearing with no active browsing pointed toward either abused browser
notification permissions or a browser-linked process running independently of any
visible window. The distinguishing detail was whether pop-ups occurred with the
browser fully closed — confirmed by later retesting that they did, which pointed
toward a source that does not require a visible browser window, such as a
malicious extension maintaining a hidden background process or an abused
notification subscription.

## 2. Action taken

- Connected to the user's machine via remote support.
- Confirmed pop-ups were occurring on the desktop as described.
- Reviewed browser notification settings and removed notification permissions
  granted to unwanted/unrecognised websites.
- Identified and removed unauthorised browser extensions associated with the
  pop-ups.
- Ran a full malware scan; the scan returned clean.

## 3. Root cause

A malicious browser extension and/or abused notification permission generating
pop-ups independent of an active, visible browser window.

Note: the malware scan came back clean. This does not rule out the extension as
the cause — adware and Potentially Unwanted Programs (PUPs) of this kind are
frequently not flagged by standard antivirus scans, which often categorise them
separately from traditional malware. A clean scan result is consistent with this
being an adware/PUP-style extension rather than evidence that no issue existed.

## 4. Verification

- Specifically retested the worst-case scenario from the original report — pop-ups
  occurring with the browser fully closed. No further pop-ups occurred.
- User confirmed the issue was resolved.

## 5. Status

**Resolved** — removing the malicious extension and notification permissions
stopped pop-ups, confirmed by retesting with the browser closed.

---

## Lessons learned

1. **Pop-ups occurring with the browser fully closed point beyond simple
   notification settings**, toward an extension or process capable of running
   independent of a visible browser window — a stronger indicator than
   notifications alone.

2. **A clean antivirus scan does not rule out adware or PUPs.** Many antivirus
   tools categorise these separately from malware and do not flag them by default;
   a clean scan should not be read as confirmation the machine is free of this
   class of issue.

3. **Retest against the original worst-case symptom, not just a general check.**
   Confirming no pop-ups specifically with the browser closed verified the fix
   against the hardest part of the reported symptom to explain, rather than a
   looser "seems fine now" check.
