---
name: update-opencode-skills
description: Use when the user asks to update, pull, sync, or refresh OpenCode skills or repositories listed in skills.paths from ~/.config/opencode/opencode.json.
compatibility: opencode
---

# Update OpenCode Skills

## When To Use

Use this skill when the user wants the local OpenCode skill repositories updated to their latest remote versions.

Trigger phrases include `update my skills`, `pull latest skills`, `sync OpenCode skills`, `refresh skills.paths`, and similar requests.

## Core Rule

Only fast-forward existing git repositories that are explicitly referenced by `skills.paths`. Never force, reset, stash, checkout another branch, create commits, or modify the OpenCode config unless the user explicitly asks.

## Workflow

1. Read `~/.config/opencode/opencode.json`.
2. Extract `skills.paths`.
3. Expand `~` and environment variables in each path.
4. For each path, check whether it exists.
5. For each existing path, find the containing repository root with `git -C <path> rev-parse --show-toplevel`.
6. Canonicalize and deduplicate repository roots before pulling.
7. For each unique repository root, check git state before updating.
8. Pull with `git pull --ff-only` only when the repo is safe to update.
9. Continue through all repositories even if one path or pull fails.
10. Report updated, skipped, missing, and failed items.

## Safety Checks

Before pulling a repository, check:

- `git -C <repo> status --porcelain` is empty.
- `git -C <repo> rev-parse --abbrev-ref HEAD` is not `HEAD`.
- `git -C <repo> rev-parse --abbrev-ref --symbolic-full-name @{u}` succeeds.

Skip and report the repository if:

- The configured path does not exist.
- The configured path is not inside a git worktree.
- The repository has staged, unstaged, or untracked changes.
- The repository is in detached HEAD state.
- The current branch has no upstream.
- `git pull --ff-only` fails because of divergence, conflicts, authentication, network errors, or another git error.

## Recommended Commands

Use commands in this shape, replacing paths as needed:

```bash
git -C "$path" rev-parse --show-toplevel
git -C "$repo" status --porcelain
git -C "$repo" rev-parse --abbrev-ref HEAD
git -C "$repo" rev-parse --abbrev-ref --symbolic-full-name @{u}
git -C "$repo" pull --ff-only
```

For quick repo discovery from the configured paths, this shell pattern is acceptable after reading the config:

```bash
for path in "$HOME/repos/example/skills"; do
  git -C "$path" rev-parse --show-toplevel
done
```

Do not use plain `git pull` because it may create merge commits. Do not assume the remote is named `origin`; use the branch's configured upstream.

## Reporting Format

End with a concise summary:

- Updated: repos pulled successfully.
- Already current: repos where `git pull --ff-only` reported no changes.
- Skipped: dirty repos, detached HEAD repos, repos without upstream, missing paths, or non-git paths.
- Failed: repos where the fast-forward pull failed.

Include the configured path when reporting missing or non-git paths, and include the repo root when reporting git status or pull results.

## Common Mistakes

- Treating each `skills.paths` entry as the repository root instead of resolving the containing git root.
- Pulling the same repository multiple times because multiple configured paths point inside it.
- Running `git pull` in a dirty worktree.
- Guessing a remote or branch when no upstream is configured.
- Stopping after the first failure instead of continuing and summarizing all outcomes.
- Claiming all skills are updated without reporting missing configured paths.
