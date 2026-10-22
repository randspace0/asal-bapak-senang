# Asal Bapak Senang

Claude Code plugin. *Asal Bapak Senang* ("as long as the boss is happy"): review PRs so the boss only sees work that passes.

## Commands

### `/abs-review <PR URL | branch | commit>`

Reviews the target for correctness bugs, security issues, edge cases, missing tests, and fit with the PR's intent.

- **Pass:** submits an approval with no body and no comments (`gh pr review --approve`).
- **Fail:** posts nothing to GitHub. Explains here, as `file:line: problem → fix`.
- Branch or commit: finds the matching PR via `gh`. No PR means nothing is submitted.

Requires the [GitHub CLI](https://cli.github.com/) (`gh`), authenticated.

## Install

```
git clone https://github.com/randspace0/asal-bapak-senang
claude --plugin-dir ./asal-bapak-senang
```

Then run `/asal-bapak-senang:abs-review <target>`.
