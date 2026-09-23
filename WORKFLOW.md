# Git Catalog Sync Workflow

1. Final `calculateLateFee`

The final function includes four changes:

```javascript
function calculateLateFee(daysLate, ratePerDay) {
  if (daysLate <= 1) {
    return 0;
  }

  const fee = Math.round(daysLate * ratePerDay);
  return Math.min(Math.max(fee, 1), 20);
}

Grace period — Task 1 / Clone A: 0 or 1 day late gives a $0 fee.
Rounding — Task 2 / Clone B: Math.floor() was changed to Math.round().
$20 maximum — Task 4 / Clone C: The fee cannot go above $20.
$1 minimum — Task 6 / Clone A: Fees after the grace period cannot be below $1.

2. Task 3 vs. Task 5 conflicts

Task 3: Two changes conflicted: the grace period and rounding. We combined both changes manually.

Task 5: Three changes had to be combined: grace period, rounding, and the $20 cap. It was harder because more changes affected the same function.

3. Task 5 merge vs. Task 6 rebase

Task 5 — Merge: Git combined two histories and created a merge commit.

Task 6 — Rebase: Git replayed the minimum-fee commit on top of the updated remote branch. After resolving the conflict, the history was rewritten and a normal push succeeded.

4. How to prevent the rejected pushes

A better process would be to use a separate branch for each change instead of having multiple clones push directly to the same shared branch. The branches could then be merged through pull requests.

Task 1:
https://github.com/JanCbns/git-catalog-sync-Cabuenas-AntonioJan/blob/main/screenshots/task-1.png?raw=true

Task 2:
https://github.com/JanCbns/git-catalog-sync-Cabuenas-AntonioJan/blob/main/screenshots/task-2.png?raw=true

Task 3:
https://github.com/JanCbns/git-catalog-sync-Cabuenas-AntonioJan/blob/main/screenshots/task-3.png?raw=true

Task 4:
https://github.com/JanCbns/git-catalog-sync-Cabuenas-AntonioJan/blob/main/screenshots/task-4.png?raw=true

Task 5:
https://github.com/JanCbns/git-catalog-sync-Cabuenas-AntonioJan/blob/main/screenshots/task-5.png?raw=true

Task 6:
https://github.com/JanCbns/git-catalog-sync-Cabuenas-AntonioJan/blob/main/screenshots/task-6.png?raw=true

Task 7:
https://github.com/JanCbns/git-catalog-sync-Cabuenas-AntonioJan/blob/main/screenshots/task-7.png?raw=true
