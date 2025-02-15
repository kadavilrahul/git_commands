# Git Guide for Beginners - Getting Started

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
