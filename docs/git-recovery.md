# Git Recovery Guide

When Git history goes wrong, do not panic. First inspect the state.

## 1. Inspect before changing anything

```bash
git status
git log --oneline --decorate --graph -n 20
git reflog
```

## 2. Accidentally committed locally?

If the commit has not been shared and you need to move HEAD back while keeping the changes staged:

```bash
git reset --soft HEAD~1
```

## 3. Need to undo a shared commit?

Prefer:

```bash
git revert <commit>
```

This creates a new commit instead of rewriting shared history.

## 4. Lost a commit after reset?

Check the reflog:

```bash
git reflog
git show <commit>
```

Then create a recovery branch at a useful reflog entry:

```bash
git branch recovery <commit>
```

## 5. Cleaning untracked files

`git clean` can permanently delete untracked content. Preview first:

```bash
git clean -n
```

Only use deletion flags after confirming the preview.

## Golden rule

Inspect first, make a backup reference when practical, and avoid rewriting shared history unless the team has agreed on it.
