---
description: Review a PR/branch/commit; approve silently if it passes, else explain here
argument-hint: "<PR URL | branch | commit>"
---

Review `$ARGUMENTS` (PR URL, branch, or commit).

1. Resolve the target: for a PR URL use `gh pr view` / `gh pr diff`; for a branch or commit use `git diff` against the base, and find its PR with `gh pr list --head <branch>` (or `gh pr list --search <sha>`).
2. Review for correctness bugs, security issues, broken edge cases, missing tests, and whether the change matches the PR's stated intent. Run the project's tests/lint if feasible and report real results.
3. Decide:
   - **Pass** (no blocking issues): submit an approval with NO body and NO comments: `gh pr review <PR> --approve`. Then reply here with one line saying it was approved. If there is no PR to approve (bare commit/branch), say it passes and that nothing was submitted.
   - **Fail**: do NOT submit anything to GitHub (no review, no comments, no request-changes). Tell me here why it did not pass, as `file:line: problem → fix`, most severe first.

Nice-to-haves and nitpicks never block approval and are never posted.
