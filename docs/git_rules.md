# Git rules for Group 24

## Working on a task
1. Never work on or push to `main` directly. `main` must always run.
2. Before starting: `git checkout main`, then `git pull`.
3. One branch per task: `feature/quality-gate`, `fix/blue-rule-removal`, `docs/contracts`.
4. Keep branches short-lived. Aim to merge in a few days.
5. Commit often, with a short message that starts with a verb:
   "Add blur check to quality gate". Avoid "update", "changes", "final".
6. Add files by name, and run `git status` before every commit.
7. Push your branch and open a pull request. Say what changed and how you tested it.

## Reviews
8. Every pull request needs one review from another member. Never merge your own.
9. Run `pytest` before asking for a review. Do not merge if tests fail.
10. Review within a day. Comment on the code, not the person.
11. After merging, delete the branch and `git pull` on `main`.

## Ownership
12. Each folder in `src/` has one owner. Others suggest changes by pull request.
13. Contracts in `docs/contracts.md` are shared. Change them only together.
14. Settings and thresholds go in `config/`, not hard-coded.

## Data and privacy
15. Never commit real photos, cleaned images of real children, consent forms,
    the name-to-code key or the real metadata sheet.
16. No names, school names, phone numbers or faces in code, comments, file
    names, commit messages, issues or screenshots. Child codes only.
17. Real data stays on the shared private drive. Do not send it in chats or email.
18. If sensitive data is committed by mistake, tell the group at once. Deleting
    it in a later commit does not remove it from history.
19. Test images in the repo must be synthetic or fully anonymous and agreed by the group.

## Conflicts
20. Merge `main` into your branch regularly.
21. Do not edit the same file as someone else at the same time. Say so in the chat.
22. Never use `git push --force` on a shared branch. Ask for help with merge conflicts.

## Tracking
23. Every task is a GitHub Issue with an owner. Link it in the pull request ("Closes #12").
24. Move your card on the board when the status changes.