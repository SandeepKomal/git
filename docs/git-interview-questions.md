# Git Interview Questions

A practical question bank for Git and DevOps interviews.

## Fundamentals

### 1. What is Git?
Git is a distributed version control system that records changes as commits and lets multiple people collaborate on the same codebase.

### 2. What is a repository?
A Git repository stores project files plus the metadata Git uses to track history, branches, references, and objects.

### 3. Working tree vs staging area vs repository?
The working tree contains your current files, the staging area is the proposed next snapshot, and the repository stores committed history.

### 4. What is a commit?
A commit is an immutable snapshot of the staged project state plus metadata such as author, timestamp, message, and parent commit references.

### 5. What is HEAD?
HEAD identifies the commit or branch currently checked out. In normal branch work, HEAD points to the current branch reference.

## Everyday commands

### 6. git fetch vs git pull?
`git fetch` downloads remote updates without integrating them into your current branch. `git pull` fetches and then integrates the updates.

### 7. git add vs git commit?
`git add` stages changes for the next snapshot. `git commit` records the staged snapshot in local history.

### 8. git clone vs git init?
`git clone` creates a local copy from an existing repository. `git init` creates a new empty local repository.

### 9. git status vs git log?
`git status` describes the current working-tree and staging state. `git log` displays commit history.

### 10. What is git remote?
It manages names and URLs for repositories outside the local repository, commonly a remote called `origin`.

## Branching

### 11. What is a branch?
A branch is a movable reference to a commit. Branches let teams work on isolated lines of development.

### 12. git switch vs git checkout?
`git switch` is focused on changing branches, while `git checkout` is a broader older command that can switch branches or restore files.

### 13. What is a fast-forward merge?
A fast-forward happens when the target branch can simply move its reference to the tip of the source branch because no divergent target commits exist.

### 14. Merge vs rebase?
Merge combines histories and preserves the branch topology. Rebase replays commits onto a new base and can create a more linear history.

### 15. When should you avoid rebase?
Avoid rebasing commits that other people are already depending on unless the team explicitly agrees and understands the history rewrite.

## Recovery

### 16. reset vs revert?
`git reset` moves branch history and can change the index or working tree. `git revert` creates a new commit that reverses an earlier commit and is usually safer for shared branches.

### 17. What does git reset --soft do?
It moves HEAD while keeping changes staged, which is useful for rebuilding or combining local commits.

### 18. What does git reset --hard do?
It moves HEAD and updates the index and working tree to match. It can discard local changes, so use it carefully.

### 19. What is git reflog?
The reflog records local movements of references such as HEAD. It is one of the most useful tools for recovering commits that appear to be lost locally.

### 20. How do you recover a deleted local commit?
Inspect `git reflog`, identify the commit, inspect it with `git show`, and create a recovery branch at that commit when appropriate.

## Collaboration

### 21. What is a pull request?
A pull request is a collaboration mechanism for proposing changes, discussing them, running checks, and reviewing code before integration.

### 22. How do you resolve a merge conflict?
Inspect the conflicted files, choose the intended content, remove conflict markers, stage the resolved files, and complete the merge or rebase.

### 23. Why use feature branches?
Feature branches isolate work, reduce accidental changes to shared branches, and provide a natural boundary for code review and CI.

### 24. What is a remote-tracking branch?
A reference such as `origin/main` records the last known state of the remote's branch in your local repository.

### 25. Why is git pull sometimes surprising?
Because it performs more than a download: it integrates remote changes using the configured merge or rebase behavior.

## Advanced

### 26. What is cherry-pick?
`git cherry-pick` applies the changes introduced by specific commits onto the current branch, creating new commit(s).

### 27. What is git bisect?
`git bisect` performs a binary search through commit history to help identify which commit introduced a bug.

### 28. What is interactive rebase useful for?
It can reorder commits, squash related commits, edit messages, or remove commits from local history before sharing it.

### 29. What is a detached HEAD?
HEAD is detached when it points directly to a commit rather than a branch. This is useful for inspecting history, but new work should usually be attached to a branch.

### 30. What is the safest mindset for destructive Git commands?
Inspect first, make a backup reference when practical, understand exactly what will change, and prefer reversible operations on shared history.

## Quick interview drill

Before an interview, make sure you can demonstrate these from a shell:

```bash
git status
git log --oneline --decorate --graph -n 20
git branch
git switch -c feature/demo
git add .
git commit -m "demo commit"
git fetch origin
git diff
git merge
git rebase
git reflog
```

The goal is not memorizing commands. Be able to explain what changes in the working tree, staging area, references, and commit graph after each operation.
