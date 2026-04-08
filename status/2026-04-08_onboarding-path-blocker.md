# Onboarding Status — 2026-04-08

## Summary

Current onboarding blocker is no longer Cadence environment setup.
The immediate next action is to confirm the actual server-side repository paths, or the official clone locations, before attempting further bridge or benchmark work.

## Verified So Far

1. VNC can connect to `thu-jin`
2. `ssh -X` to `thu-wu` works
3. After `source /home/cshrc/.cshrc.cadence.IC618SP201`, both `which spectre` and `which virtuoso` resolve normally

## Current Blocker

The following project repositories or working directories have not yet been located on the server side:

1. `vaEvas`
2. `behavioral-veriloga-eval`
3. `sshConnect/virtuoso-bridge-lite`

Without the actual paths, the onboarding docs that use `cd <repo>/...` remain underspecified for a new member.

## Team Recommendation

Before doing more environment trial-and-error, ask the senior student or repository owner for one of the following:

1. The exact server paths of the working repositories
2. The Git clone URLs
3. The expected destination directory in the new member's account

## Suggested Message

```text
我现在已经成功做到这一步了：
1. VNC 能连上 thu-jin
2. 能 ssh -X 到 thu-wu
3. source /home/cshrc/.cshrc.cadence.IC618SP201 之后，which spectre 和 which virtuoso 都正常

现在我这边还没找到项目仓库目录，比如 vaEvas、behavioral-veriloga-eval、sshConnect/virtuoso-bridge-lite。
麻烦告诉我这些仓库在服务器上的实际路径，或者我应该从哪里 clone / 拷贝到自己的目录。
```

## Follow-up

Once the repository paths are confirmed, the next onboarding action is:

1. Enter the actual repository root
2. Check `git remote -v`
3. Complete bridge smoke test
4. Run one minimal EVAS-first closed-loop example
