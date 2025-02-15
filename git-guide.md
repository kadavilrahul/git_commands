# Git Guide for Beginners

This guide helps you get started with Git, a tool for tracking code changes and collaboration. Git saves versions of your project, allowing you to revert to earlier states and work with others, especially on platforms like GitHub.

Let's learn the basics step-by-step.

## 1. Getting Started with Git

This section covers the initial setup and basic local operations.

### Install Git

Install Git on your computer. For Linux, use these commands:

```bash
sudo apt update
sudo apt install git
git --version
```

*   **`sudo apt update`**: Update software list (Linux).
*   **`sudo apt install git`**: Install Git (Linux).
*   **`git --version`**: Check Git installation.

For Windows or macOS, download from [https://git-scm.com/downloads](https://git-scm.com/downloads) and follow instructions.

### Configure Git - Set Up Identity

Tell Git who you are for commit authorship.

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

*   **`git config --global user.name "Your Name"`**: Set your name for Git.
*   **`git config --global user.email "your.email@example.com"`**: Set your email for Git (use GitHub email if applicable).

Check configuration:

```bash
git config --global --list
```

### Initialize Git Repository

Turn your project folder into a Git repository. In your project folder, run:

```bash
git init
```

*   **`git init`**: Initialize a new Git repository in the current folder.  Run once per project.

Check if a folder is a Git repository:

```bash
git rev-parse --is-inside-work-tree
```

### Check Project Status

See the current state of your project.

```bash
git status
```

*   **`git status`**: Show repository status: untracked files, changes not staged, changes to commit, current branch.

### Stage Changes

Prepare changes for the next commit.

```bash
git add .
```

*   **`git add .`**: Stage all changes in the current directory. Use `git add <filename>` for specific files.

### Commit Changes - Save Progress

Save staged changes as a new commit (snapshot).

```bash
git commit -m "Your commit message"
```

*   **`git commit -m "Your commit message"`**: Save staged changes as a commit. Write clear commit messages describing changes (e.g., "Fix typo", "Add user login").

### View Commit History

See commit history.

```bash
git log
```

*   **`git log`**: Show commit history (newest first), including commit hash, author, date, and message.

For a shorter view:

```bash
git log --oneline
```

*   **`git log --oneline`**: Show commit history in one line per commit.

## 2. Working with Remote Repositories

This section explains how to connect to and work with remote repositories like GitHub.

### Add Remote Repository

Connect local repository to a remote repository on GitHub. Get repository URL from GitHub (e.g., `https://github.com/username/repository_name.git`).

```bash
git remote add origin https://github.com/username/repository_name.git
```

*   **`git remote add origin https://github.com/username/repository_name.git`**: Add a remote repository named `origin`. Replace URL with your GitHub repository URL.

Verify remote URL:

```bash
git remote -v
```

*   **`git remote -v`**: Show configured remote repositories and URLs.

### Push Changes to Remote Repository

Upload local commits to GitHub.

```bash
git push --set-upstream origin main
```

*   **`git push --set-upstream origin main`**: Push commits to the `main` branch of the `origin` remote.  Required for the first push from a new local branch.  Later, use `git push origin main` or just `git push`.

Use a Personal Access Token (PAT) instead of password for security (generate in GitHub settings).

### Clone a Repository - Download from GitHub

Download a project from GitHub to your computer.

```bash
git clone https://github.com/username/repository_name.git
cd repository_name
```

*   **`git clone https://github.com/username/repository_name.git`**: Clone (download) a repository from the given URL.
*   **`cd repository_name`**: Go to the cloned repository folder.

### Pulling Changes from Remote

Get changes from a remote repository.

```bash
git pull origin main
```

*   **`git pull origin main`**: Fetch and merge changes from the `main` branch on `origin` into your current branch.  You can often use `git pull` if your local branch is tracking `origin/main`.

## 3. Collaborating with Branches

This section introduces branching for parallel development and collaboration.

### Create New Branch

Create and switch to a new branch.

```bash
git checkout -b <new-branch-name>
```

*   **`git checkout -b <new-branch-name>`**: Create a new branch named `<new-branch-name>` and switch to it (e.g., `feature-x`, `fix-y`).

### Switch Between Branches

Switch to an existing branch.

```bash
git checkout <branch-name>
```

*   **`git checkout <branch-name>`**: Switch to branch `<branch-name>` (e.g., `main`, `feature-x`).

### List Branches

List branches.

```bash
git branch
```

*   **`git branch`**: List local branches. Current branch marked with `*`.

List local and remote branches:

```bash
git branch -a
```

*   **`git branch -a`**: List all branches (local and remote).

### Push New Branch to Remote

Upload a new local branch to the remote repository.

```bash
git push --set-upstream origin <branch-name>
```

*   **`git push --set-upstream origin <branch-name>`**: Push local branch `<branch-name>` to `origin`. Required for the first push of a new branch. Later, use `git push`.

## 4. More Useful Git Features

This section covers some additional helpful Git commands.

### Stash Changes Temporarily

Temporarily save uncommitted changes.

```bash
git stash
```

*   **`git stash`**: Save uncommitted changes.

List stashes:

```bash
git stash list
```

*   **`git stash list`**: Show list of stashes.

Apply latest stash:

```bash
git stash apply
```

*   **`git stash apply`**: Apply the latest stash (keeps stash).

Apply and remove latest stash:

```bash
git stash pop
```

*   **`git stash pop`**: Apply and remove the latest stash.

Remove a specific stash:

```bash
git stash drop <stash-id>
```
*(Find `stash-id` from `git stash list`)*

Clear all stashes:

```bash
git stash clear
```

### View Specific Commit

See details of a commit.

```bash
git show <commit-hash>
```

*   **`git show <commit-hash>`**: Show commit details for `<commit-hash>`.

### Remove Files from Git Tracking (Keep Locally)

Stop tracking files but keep them locally.

```bash
git rm --cached <file-pattern>
```

*   **`git rm --cached <file-pattern>`**: Stop tracking files matching `<file-pattern>` (e.g., `git rm --cached secrets.txt`).

### Tagging Commits

Mark important points in history, like releases.

**Create lightweight tag:**

```bash
git tag <tag-name>
```

**Create annotated tag (for releases):**

```bash
git tag -a <tag-name> -m "Tag message"
```

**Push tags to remote:**

```bash
git push origin --tags
```

### Credential Management - Securely Store GitHub Token (Optional)

Secure authentication with GitHub using Personal Access Token (PAT). Use credential manager to store token.

```bash
git config --global credential.helper manager-core
```

*   **`git config --global credential.helper manager-core`**: Configure Git to use Git Credential Manager Core for secure token storage. Install Git Credential Manager Core if needed.

## Conclusion

This guide covers basic Git commands and workflows. Practice and explore more features as you get comfortable. Happy coding!
