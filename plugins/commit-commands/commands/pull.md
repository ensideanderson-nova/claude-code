---
allowed-tools: Bash(git pull:*), Bash(git status:*), Bash(git fetch:*)
description: Pull changes from the remote repository
---

## Context

- Current branch: !`git branch --show-current`
- Current git status: !`git status`
- Remote tracking info: !`git branch -vv`

## Your task

Pull the latest changes from the remote repository for the current branch.

1. First, check if the current branch has a remote tracking branch using `git branch -vv`
2. If it does, run `git pull` to fetch and merge changes from the remote
3. If there's no remote tracking branch, inform the user that the branch has no upstream and suggest setting it up with `git branch --set-upstream-to=origin/<branch>` or pushing with `git push -u origin <branch>`
4. Show the status after pulling to confirm the operation

Execute all necessary commands efficiently. If there are issues (no tracking branch, merge conflicts, etc.), provide clear feedback to the user about what happened and what they need to do.
