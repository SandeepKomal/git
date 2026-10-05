# GitHub & Collaboration Workflow Commands

Commands used for the GitHub workflows across projects in this workspace.

## Identity and account switching

### Git commit identity

```bash
git config user.name "Your Name"
git config user.email "you@example.com"
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### GitHub CLI authentication

```bash
gh auth status
gh auth login
gh auth logout
gh api user --jq .login
```

> Git commit identity and GitHub authentication are separate. Changing `git config user.email` does not switch the GitHub account you are authenticated as.

## Branch workflow

```bash
git switch main
git pull --ff-only origin main
git switch -c feature/name
git push -u origin feature/name
```

Change an existing branch:

```bash
git switch main
git switch feature/name
```

Refresh remote branches:

```bash
git fetch --prune origin
git branch -a
```

## Pull requests with GitHub CLI

```bash
gh pr create --base main --head feature/name
gh pr list
gh pr status
gh pr view <number>
gh pr checkout <number>
gh pr diff <number>
gh pr checks <number>
gh pr merge <number>
```

## GitHub Actions

```bash
gh workflow list
gh run list
gh run watch <run-id>
gh run view <run-id>
gh run view <run-id> --log
gh run rerun <run-id> --failed
```

## Releases and tags

```bash
git tag -a v1.0.0 -m "Release v1.0.0"
git push origin v1.0.0
gh release create v1.0.0 --generate-notes
```

## Co-authoring commits

```bash
git commit -m "feat: collaborative change

Co-authored-by: Contributor One <one@example.com>
Co-authored-by: Contributor Two <two@example.com>"
```

## Fork / remote workflow

Check remotes:

```bash
git remote -v
```

Add upstream:

```bash
git remote add upstream https://github.com/UPSTREAM/REPO.git
```

Sync with upstream:

```bash
git fetch upstream
git switch main
git merge upstream/main
```

## Repository housekeeping

Delete merged local branch:

```bash
git branch -d feature/name
```

Delete remote branch:

```bash
git push origin --delete feature/name
```

Prune deleted remote references:

```bash
git fetch --prune
```

## Useful diagnostics

```bash
git status
git remote -v
git branch -vv
git log --oneline --decorate --graph --all -n 30
git reflog
gh auth status
gh api user --jq .login
```

## Safe update routine

Before starting work:

```bash
git switch main
git pull --ff-only origin main
git fetch --prune origin
git switch -c feature/name
```

Before opening a PR:

```bash
git status
git diff
git diff --staged
git push -u origin feature/name
gh pr create --base main --head feature/name
```

After a PR is merged:

```bash
git switch main
git pull --ff-only origin main
git branch -d feature/name
git fetch --prune
```
