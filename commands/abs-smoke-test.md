---
description: Smoke test a PR on an Android device, capture screenshots/video, draft the PR comment
argument-hint: "<PR URL | number | branch>"
---

Smoke test `$ARGUMENTS` on a connected Android device and prepare evidence for the PR.

1. **Device lock:** run `~/.claude/bin/devlock acquire abs-smoke-test`. If it prints BUSY, stop and tell me. Release with `~/.claude/bin/devlock release abs-smoke-test` at the end, including on failure.
2. **Checklist:** read `gh pr view` and `gh pr diff`. Derive a short smoke checklist (changed screens/flows plus app-launch sanity). Show it before running.
3. **Build and install:** abort if the working tree is dirty. `gh pr checkout`, then use the `android-cli` skill to build, install and launch. No device or emulator: report and stop, post nothing.
4. **Exercise:** walk the checklist. For each step take a screenshot (`adb exec-out screencap -p`) and note PASS/FAIL. Record the flow with `adb shell screenrecord`, pull the mp4, and convert it to a GIF with `ffmpeg` if available. Check `logcat` for FATAL/ANR/crashes.
5. **Save media** locally in the scratchpad under `pr-<N>/<timestamp>/`.
6. **Draft the PR comment (do not post):** device and build info, checklist table with PASS/FAIL, embedded screenshots/GIF, link to the mp4, any crash excerpt. Show it with the list of files.
7. **Only after I say yes:**
   - Push the media to orphan branch `abs-smoke-media` under `pr-<N>/<timestamp>/`, using a temporary git worktree so the current checkout is untouched.
   - Post one comment with `gh pr comment`, embedding `https://github.com/<org>/<repo>/blob/abs-smoke-media/<path>?raw=true` URLs (these render for signed-in viewers, so they work on private repos).

Rules: never approve, request changes, or comment on code. The only GitHub writes are the media push and the single confirmed comment. A GIF embeds inline; an mp4 is only a link.
