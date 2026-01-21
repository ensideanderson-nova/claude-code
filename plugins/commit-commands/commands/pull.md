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

1. First, check if the current branch has a remote tracking branch
2. If it does, run `git pull` to fetch and merge changes from the remote
3. If there's no remote tracking branch, inform the user and suggest running `git pull origin <branch-name>` manually
4. Show the status after pulling to confirm the operation

You have the capability to call multiple tools in a single response. Execute all necessary commands in a single message. Do not use any other tools or do anything else. Do not send any other text or messages besides these tool calls.
