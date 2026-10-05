# Git Commands & Interview Questions

Practical Git commands, concepts, and interview preparation notes for developers, DevOps engineers, cloud engineers, and students.

[![GitHub stars](https://img.shields.io/github/stars/SandeepKomal/git?style=flat-square)](https://github.com/SandeepKomal/git/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/SandeepKomal/git?style=flat-square)](https://github.com/SandeepKomal/git/network/members)
[![GitHub issues](https://img.shields.io/github/issues/SandeepKomal/git?style=flat-square)](https://github.com/SandeepKomal/git/issues)
[![License](https://img.shields.io/github/license/SandeepKomal/git?style=flat-square)](LICENSE)

> A compact, practical Git reference you can keep open while working — plus interview questions for revision.

## Why this repository?

Git knowledge is often split between documentation, cheat sheets, and interview notes. This repository brings the most useful day-to-day commands and core concepts into one small, searchable reference.

Use it to:

- Refresh Git commands quickly.
- Prepare for Git and DevOps interviews.
- Learn the difference between similar commands.
- Find recovery commands when something goes wrong.
- Contribute examples that help other engineers.

## What's inside?

| Resource | Purpose |
| --- | --- |
| **GIT Commands.txt** | Command-focused reference with explanations |
| **Git Commands** | Plain-text command reference |
| **GIT Theory & Interview Questions.docx** | Theory and interview-preparation material |

## Quick start

Clone the repository:

```bash
git clone https://github.com/SandeepKomal/git.git
cd git
```

Start with these commands:

```bash
git status
git add .
git commit -m "message"
git push
```

## Essential Git workflow

```text
Working tree
   |
   | git add
   v
Staging area
   |
   | git commit
   v
Local repository
   |
   | git push
   v
Remote repository
```

## Command index

### Everyday workflow

| Command | Use it for |
| --- | --- |
| `git status` | Check changed and staged files |
| `git add` | Stage changes |
| `git commit` | Save a snapshot to history |
| `git push` | Publish local commits |
| `git pull` | Fetch and integrate remote changes |
| `git fetch` | Download remote changes without integrating |
| `git clone` | Create a working copy of a repository |

### Branching & integration

| Command | Use it for |
| --- | --- |
| `git branch` | Create and manage branches |
| `git switch` | Move between branches |
| `git merge` | Combine branch histories |
| `git rebase` | Replay commits onto another base |
| `git rebase -i` | Clean up or edit local commit history |

### Recovery & maintenance

| Command | Use it for |
| --- | --- |
| `git reset` | Move HEAD and optionally update staging/worktree |
| `git revert` | Create a new commit that undoes an earlier commit |
| `git stash` | Temporarily save uncommitted work |
| `git stash pop` | Reapply and remove a stash |
| `git stash apply` | Reapply a stash while keeping it |
| `git clean` | Remove untracked files |
| `git log` | Inspect commit history |
| `git config` | Manage Git configuration |

## Important safety note

Git commands such as `reset --hard`, `clean -fd`, and history-rewriting commands can permanently remove local work.

Before destructive operations:

```bash
git status
git log --oneline -n 10
git branch backup-before-change
```

## Interview preparation

The repository also includes a dedicated theory/interview resource. Focus on understanding:

- Working tree vs staging area vs repository
- Merge vs rebase
- Reset vs revert
- Fetch vs pull
- Local vs remote branches
- HEAD, refs, and commit history
- Stash workflows
- Conflict resolution
- Rewriting local history safely

### Example interview question

**Q: What is the difference between `git fetch` and `git pull`?**

**A:** `git fetch` downloads remote updates without changing your current branch. `git pull` performs a fetch and then integrates the fetched changes into the current branch.

## Roadmap

Planned improvements:

- [ ] Convert command notes into structured Markdown pages.
- [ ] Add real-world Git troubleshooting scenarios.
- [ ] Add a larger interview question bank.
- [ ] Add diagrams for Git internals and branching.
- [ ] Add beginner, intermediate, and advanced learning paths.
- [ ] Add more tested command examples.

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

This project is available under the [MIT License](LICENSE).

## Support the project

Found this useful? A GitHub star helps other developers discover the project.

**Star the repository:** https://github.com/SandeepKomal/git

Built as a practical learning resource for the developer community.
