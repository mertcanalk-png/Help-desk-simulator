# Ticket 35 — "You Don't Have Access" to Shared Drive (Stale Credential, Not Permissions)

> Self-directed simulator practice. Fictional data. Not paid work.

| Field | Detail |
|---|---|
| Priority | Medium |
| Category | Network / Access |
| Reported symptom | User cannot open the shared department drive; clicking it returns "you don't have access." |

---

## 1. Diagnosis

The error wording suggested an authorization problem — a genuine "you don't have
access" message typically points to missing group membership or folder
permissions, a different category of fault from a connectivity or mapping issue.
Rather than assuming this and jumping to a fix, the user's group membership and
the folder's permissions were checked directly in the directory first.

Permissions were confirmed to be genuinely intact — the account had the
correct access. This ruled out a true authorization failure and redirected the
diagnosis: with valid permissions confirmed, the most consistent explanation for
an access-denied-looking symptom is a stale or mismatched cached credential on the
existing drive connection, which produces an identical-looking failure to the user
without any actual permissions problem being present.

## 2. Root cause

A stale cached credential on the existing network drive connection, presenting as
an access-denied error despite the account's underlying permissions being valid
throughout.

## 3. Action taken

- Checked the user's group membership and the shared folder's permissions in the
  directory; confirmed access was genuinely valid.
- Remapped the network drive
  (`\\FILESERV01\departments\Support`), forcing a fresh authentication with
  current credentials rather than relying on the existing, stale connection.

## 4. Verification

- User confirmed the shared drive was reachable and documents were accessible
  after remapping.

## 5. Status

**Resolved** — fresh drive mapping resolved the access error; underlying
permissions were confirmed valid throughout and were never the cause.

---

## Lessons learned

1. **"Access denied" wording does not guarantee a permissions problem.** Checking
   actual group membership and folder permissions before acting confirmed this was
   not a true authorization failure, avoiding an incorrect diagnosis based on the
   error message alone.

2. **A stale cached credential can produce a symptom identical to a genuine
   permissions error.** The two require different fixes — remapping resolves a
   stale credential; restoring group membership resolves a genuine permissions
   gap. Confirming which one is present before acting prevents applying the wrong
   fix.

3. **Verify before diagnosing by category.** The distinction between an
   unreachable resource, a lost mapping, and a genuine permissions failure matters,
   because each requires a different fix — checking permissions directly, rather
   than inferring from the error message, was what correctly identified this case.
