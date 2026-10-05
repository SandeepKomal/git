# Git Commands

A practical command reference for everyday Git, GitHub collaboration, branching, recovery, identity switching, and the workflows used across the projects in this account.

## 1. First-time setup

### Check Git

```bash
git --version
```

### Set your global identity

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### View configuration

```bash
git config --global --list
git config --list --show-origin
```

### Change the Git account used for commits

Git commit identity is configured separately from the GitHub account you authenticate with.

For one repository:

```bash
git config user.name "Your Name"
git config user.email "you@example.com"
```

For all repositories:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Verify:

```bash
git config user.name
git config user.email
```

> Changing `user.name` and `user.email` changes the author identity on **new commits**. It does not rewrite old commits.

## 2. Create or clone a repository

```bash
git init
git clone https://github.com/OWNER/REPO.git
git clone git@github.com:OWNER/REPO.git
cd REPO
```

## 3. Inspect your repository

```bash
git status
git log --oneline
git log --oneline --decorate --graph --all
git show <commit>
git diff
git diff --staged
git remote -v
git branch
git branch -a
```

## 4. Stage and commit changes

```bash
git add file.txt
git add .
git add -A
git restore --staged file.txt
git commit -m "feat: add new feature"
git commit --amend
```

Before amending a shared commit, make sure rewriting that history is appropriate.

## 5. Work with branches

Create and switch:

```bash
git switch -c feature/my-change
git switch main
```

Older equivalent:

```bash
git checkout -b feature/my-change
```

List branches:

```bash
git branch
git branch -a
git branch -r
```

Rename a branch:

```bash
git branch -m old-name new-name
```

Delete a local branch:

```bash
git branch -d feature/my-change
git branch -D feature/my-change
```

Delete a remote branch:

```bash
git push origin --delete feature/my-change
```

## 6. Switch branches and update from remote

```bash
git fetch origin
git switch main
git pull --ff-only origin main
git switch feature/my-change
```

Create a local branch from a remote branch:

```bash
git switch -c feature/my-change --track origin/feature/my-change
```

## 7. Remote repositories

Add a remote:

```bash
git remote add origin https://github.com/OWNER/REPO.git
```

Change a remote URL:

```bash
git remote set-url origin https://github.com/OWNER/REPO.git
```

Using SSH:

```bash
git remote set-url origin git@github.com:OWNER/REPO.git
```

Inspect:

```bash
git remote -v
git remote show origin
```

## 8. Push changes to GitHub

First push for a branch:

```bash
git push -u origin main
git push -u origin feature/my-change
```

Later pushes:

```bash
git push
```

Push a tag:

```bash
git push origin v1.0.0
git push origin --tags
```

## 9. Fetch vs pull

Fetch without changing your current branch:

```bash
git fetch origin
```

Fetch and integrate:

```bash
git pull
```

A safer explicit workflow:

```bash
git fetch origin
git log --oneline HEAD..origin/main
git merge origin/main
```

## 10. Merge

```bash
git switch main
git pull --ff-only
git merge feature/my-change
git push
```

Abort a merge in progress:

```bash
git merge --abort
```

## 11. Rebase

Update a feature branch:

```bash
git fetch origin
git switch feature/my-change
git rebase origin/main
```

Continue after resolving conflicts:

```bash
git add <resolved-file>
git rebase --continue
```

Abort:

```bash
git rebase --abort
```

Interactive cleanup:

```bash
git rebase -i HEAD~5
```

> Do not casually rebase commits that other people have already based work on.

## 12. Undo changes

Discard changes in one file:

```bash
git restore file.txt
```

Unstage a file:

```bash
git restore --staged file.txt
```

Create a new commit that undoes another commit:

```bash
git revert <commit>
```

Move HEAD while keeping changes staged:

```bash
git reset --soft HEAD~1
```

Move HEAD and keep changes unstaged:

```bash
git reset --mixed HEAD~1
```

Destructive reset:

```bash
git reset --hard HEAD~1
```

> Prefer `git revert` for shared history. Treat `reset --hard` as destructive.

## 13. Stash

Save work:

```bash
git stash push -m "WIP: feature"
```

List:

```bash
git stash list
```

Apply and keep stash:

```bash
git stash apply stash@{0}
```

Apply and remove stash:

```bash
git stash pop
```

Delete one stash:

```bash
git stash drop stash@{0}
```

Delete all stashes:

```bash
git stash clear
```

## 14. Recover lost commits

Inspect reference history:

```bash
git reflog
```

Inspect the commit:

```bash
git show <commit>
```

Create a recovery branch:

```bash
git switch -c recovery/<name> <commit>
```

## 15. Cherry-pick

Apply a specific commit to the current branch:

```bash
git cherry-pick <commit>
```

Abort:

```bash
git cherry-pick --abort
```

Continue after conflict resolution:

```bash
git add <resolved-file>
git cherry-pick --continue
```

## 16. Tags and releases

Create an annotated tag:

```bash
git tag -a v1.0.0 -m "Release v1.0.0"
```

List tags:

```bash
git tag
git show v1.0.0
```

Push:

```bash
git push origin v1.0.0
```

## 17. Clean untracked files

Preview:

```bash
git clean -n
```

Delete untracked files:

```bash
git clean -f
```

Delete untracked files and directories:

```bash
git clean -fd
```

> Always preview with `-n` first.

## 18. Co-author commits

Add one co-author:

```bash
git commit -m "feat: improve deployment workflow

Co-authored-by: Name <email@example.com>"
```

Multiple co-authors:

```bash
git commit -m "feat: collaborate on feature

Co-authored-by: First Contributor <first@example.com>
Co-authored-by: Second Contributor <second@example.com>"
```

The `Co-authored-by:` trailer must be formatted correctly for GitHub to attribute the contribution.

## 19. GitHub authentication

Check GitHub CLI authentication:

```bash
gh auth status
```

Login:

```bash
gh auth login
```

Switch between GitHub CLI accounts:

```bash
gh auth logout
gh auth login
```

For multiple accounts, use separate SSH keys/hosts or the GitHub CLI's account-aware authentication rather than repeatedly changing commit identity.

Check the GitHub CLI account:

```bash
gh api user --jq .login
```

> Commit identity (`git config user.*`) and GitHub authentication (`gh auth` / SSH credentials) are different concepts.

## 20. Working with GitHub repositories

Clone:

```bash
gh repo clone OWNER/REPO
```

Create:

```bash
gh repo create
```

Open repository in browser:

```bash
gh repo view --web
```

Create a pull request:

```bash
gh pr create --base main --head feature/my-change
```

Check PR status:

```bash
gh pr status
```

View a PR:

```bash
gh pr view <number>
```

Checkout a PR:

```bash
gh pr checkout <number>
```

Merge a PR:

```bash
gh pr merge <number>
```

## 21. GitHub Actions workflows

Check workflow runs:

```bash
gh run list
```

Watch a workflow:

```bash
gh run watch
```

View a failed workflow:

```bash
gh run view <run-id>
```

Retry failed jobs:

```bash
gh run rerun <run-id> --failed
```

## 22. Common project workflow

Use this for the type of GitHub projects built in this workspace:

```bash
git switch main
git pull --ff-only origin main
git switch -c feature/my-change

# edit files

git status
git diff
git add .
git commit -m "feat: implement change"
git push -u origin feature/my-change

gh pr create --base main --head feature/my-change
```

After merge:

```bash
git switch main
git pull --ff-only origin main
git branch -d feature/my-change
```

## 23. Emergency checklist

Before risky commands:

```bash
git status
git log --oneline --decorate --graph -n 20
git reflog
git branch backup-before-change
```

Use `revert` for shared history, and use `reset --hard`, `clean -fd`, and force-push operations only when you understand exactly what they will remove or rewrite.
