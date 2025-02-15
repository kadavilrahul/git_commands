# Git Guide for Beginners - Getting Started

This section covers the initial setup and basic local operations.

### Install Git

Install Git on your Linux machine:

```bash
sudo apt update
sudo apt install git
git --version
```

For Windows or macOS, download from [https://git-scm.com/downloads](https://git-scm.com/downloads) and follow instructions.

**Verify Installation**

After installation, verify that Git is correctly installed by checking the version:

```bash
git --version
```
This command should output the installed Git version, confirming successful installation.

### Configure Git - Set Up Identity

Tell Git who you are for commit authorship.

```bash
git config --global user.name "Your Name"
```
```bash
git config --global user.email "your.email@example.com"
```

Check configuration if it's updated:

```bash
git config --global --list
```

### Default Branch Name

By default, Git may initialize new repositories with a branch named `master`.

To check your default initial branch name, use:

```bash
git config --global init.defaultBranch
```

If you want to set a specific default branch name for all new repositories you create, you can use:

```bash
git config --global init.defaultBranch main
```
Replace `main` with your desired default branch name if needed. If you don't set this, Git will use its default (which might be `main` or `master` depending on your Git version and settings).

### Configure Default Editor (Optional)

Git uses a text editor to write commit messages and for other operations. Git will try to use your system's default editor. You can configure a specific editor if you prefer.

To check your current default editor, use:

```bash
git config --global core.editor
```

To set a specific editor, for example, Visual Studio Code, you can use:

```bash
git config --global core.editor "code --wait"
```

Or for other editors, like Nano:

```bash
git config --global core.editor "nano"
```

Choose your preferred editor and configure it using the appropriate command.

### Initialize Git Repository

Turn your project folder into a Git repository. Run once per project.
In your project folder, run:

```bash
git init
```

Check if a folder is a Git repository:

```bash
git rev-parse --is-inside-work-tree
```
Should get response as true

### Check Project Status

See the current state of your project. See repository status, untracked files, changes not staged, changes to commit, current branch.

```bash
git status
```

### Stage Changes

Prepare changes for the next commit.
For all files:
```bash
git add .
```
For specific files:
```bash
git add <filename>
```

### Commit Changes - Save Progress

Save staged changes as a new commit (snapshot).

```bash
git commit -m "Your commit message"
```
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
