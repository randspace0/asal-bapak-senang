# Asal Bapak Senang

![Asal Bapak Senang](https://i.ytimg.com/vi/9f4Hcor_Ins/oardefault.jpg?sqp=-oaymwEYCJUDENAFSFqQAgHyq4qpAwcIARUAAIhC&rs=AOn4CLAZdOD-BXobFFBbqGPc9mKIQ2ewSw&usqp=CCk)

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
/plugin marketplace add randspace0/asal-bapak-senang
/plugin install asal-bapak-senang --marketplace randspace0/asal-bapak-senang
```

Then run `/asal-bapak-senang:abs-review <target>`.

Or try locally without installing: `claude --plugin-dir ./asal-bapak-senang`.
