---
name: repo-clone-location
description: Clone repositories into ~/repos/<author>/<repo> by default, with explicit root clone handling.
compatibility: opencode
---

## When To Use

Use this skill whenever the user asks to clone a repository.

## Clone Location Rules

- Default root for all repository clones is `~/repos`.
- For a normal clone request, derive the author or owner from the repository URL and clone into `~/repos/<author>/<repo>`.
- Example: `https://github.com/ahd3r/crd-lrn.git` has author `ahd3r`, so clone it into `~/repos/ahd3r/crd-lrn`.
- If `~/repos/<author>` does not exist, create it before cloning.
- If `~/repos/<author>` already exists, check whether it is a grouping folder containing repositories or a Git repository itself.
- If `~/repos/<author>` is a Git repository itself, ask the user what to do before creating `~/repos/<author>/<repo>` or cloning anywhere else.
- If the user explicitly asks to clone the repository "in root", clone directly into `~/repos/<repo>` and do not create or use an author directory.

## Existing Directory Handling

- Before cloning, check whether the target directory already exists.
- For normal author-folder clones, if the exact target already exists, ask the user how to proceed before cloning again.
- For normal author-folder clones, if the author folder exists as a repository cloned directly under `~/repos`, treat that as a conflict and ask the user whether to rename/move the existing repo, choose another destination, or cancel.
- For explicit root clones, if `~/repos/<repo>` already exists, ask the user whether they still want to clone it because it is already there.
- If the user confirms an explicit root clone despite an existing directory, choose the first available incremented directory name by appending a number to the repo name, such as `~/repos/<repo>2`, `~/repos/<repo>3`, and so on.

## Implementation Notes

- Accept common GitHub URL forms, including HTTPS URLs ending in `.git` and SSH URLs like `git@github.com:author/repo.git`.
- Strip a trailing `.git` from the repository directory name.
- Use non-interactive commands for filesystem checks and cloning.
