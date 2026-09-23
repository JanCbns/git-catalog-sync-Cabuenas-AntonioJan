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
<img width="1919" height="1079" alt="Task 1" src="https://github.com/user-attachments/assets/12440da9-7550-4a74-abb0-b38155e58789" />

Task 2:
<img width="1919" height="1079" alt="Task 2" src="https://github.com/user-attachments/assets/96e023ae-7398-44b9-a270-ce397abb5c0c" />

Task 3:
<img width="1919" height="1079" alt="Task 3" src="https://github.com/user-attachments/assets/469f5b36-892d-4bd4-b9d5-99528a10167c" />

Task 4:
<img width="1919" height="1079" alt="Task 4" src="https://github.com/user-attachments/assets/a21c31cd-91c4-4759-a119-b0931415ece9" />

Task 5:
<img width="1919" height="1079" alt="Task 5" src="https://github.com/user-attachments/assets/5fb075e9-c254-4cd2-9fa8-4ff8187326a3" />

Task 6:
<img width="1919" height="1079" alt="task 6" src="https://github.com/user-attachments/assets/1cee1f72-7f56-4398-98a6-285c1aa2015a" />

Task 7:
<img width="1919" height="1079" alt="Task 7" src="https://github.com/user-attachments/assets/592c30de-4d77-4ccd-8a37-79e15d77f240" />
