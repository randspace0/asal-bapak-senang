# Asal Bapak Senang

Claude Code plugin. *Asal Bapak Senang* ("as long as the boss is happy"): review PRs so the boss only sees work that passes.

## Commands

### `/abs-review <PR URL | branch | commit>`

Reviews the target for correctness bugs, security issues, edge cases, missing tests, and fit with the PR's intent.

- **Pass:** submits an approval with no body and no comments (`gh pr review --approve`).
- **Fail:** posts nothing to GitHub. Explains here, as `file:line: problem → fix`.
- Branch or commit: finds the matching PR via `gh`. No PR means nothing is submitted.

Requires the [GitHub CLI](https://cli.github.com/) (`gh`), authenticated.

### `/abs-smoke-test <PR URL | number | branch>`

Smoke tests a PR on a connected Android device.

- Derives a checklist from the PR and shows it first.
- Builds, installs and exercises the app; captures screenshots, a screen recording and crash logs.
- Drafts a PR comment with PASS/FAIL and the media. Nothing is pushed or posted until you confirm.
- On confirm, media goes to the `abs-smoke-media` orphan branch and one comment is posted.

Requires `adb`, the `android-cli` skill, `devlock`, and optionally `ffmpeg` (for GIFs).

## Install

```
git clone https://github.com/randspace0/asal-bapak-senang
claude --plugin-dir ./asal-bapak-senang
```

Then run `/asal-bapak-senang:abs-review <target>`.
