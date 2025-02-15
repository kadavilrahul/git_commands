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

### .gitignore - Ignoring Files

It's often necessary to exclude certain files and directories from being tracked by Git, such as temporary files, build outputs, or sensitive information. You can do this by creating a `.gitignore` file in the root of your repository.

**Create .gitignore file**
In your project root, create a file named `.gitignore`.

```bash
touch .gitignore
```

Then, open `.gitignore` with a text editor and add patterns for files and directories you want Git to ignore.

**Common entries for .gitignore**
Here are some common examples of entries you might add to your `.gitignore` file:

```
node_modules/   # Ignore the node_modules directory (common in Node.js projects)
*.log           # Ignore all files with the .log extension (log files)
.env            # Ignore .env files (environment configuration files)
.DS_Store        # Ignore .DS_Store files (macOS folder metadata files)
build/          # Ignore the build directory (common for build outputs)
dist/           # Ignore the dist directory (common for distribution packages)
tmp/            # Ignore temporary files and directories
*.swp           # Ignore swap files (e.g., created by Vim)
```

Each line in `.gitignore` represents a pattern. Git will ignore files and directories that match these patterns. You can use wildcards (`*`, `?`, `[]`) and specify directory names to create flexible ignore rules.

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
```bash
git log --pretty=format:"%h %ad %s" --date=format:"%Y-%m-%d %H:%M:%S"
```

### Viewing Changes

Git provides commands to view changes you've made in your working directory and staging area. This is helpful to review your modifications before committing.

**View changes before staging**
To see changes in your working directory that are not yet staged, use `git diff`.

```bash
git diff
```
This command displays the differences between your working directory and the last commit. It shows line-by-line changes, additions, and deletions.

**View staged changes**
To see changes that are staged and ready to be committed, use `git diff --staged`.

```bash
git diff --staged
```
This command shows the differences between the staging area and the last commit. It's useful to verify what you've added to the staging area before committing.

**View changes in a specific file**
To view changes for a specific file, you can specify the filename with `git diff`.

```bash
git diff <filename>
```
This will show the changes made to the specified file compared to the last commit. You can also use `--staged` to view staged changes for a specific file:

```bash
git diff --staged <filename>
```

### Undoing Changes

Git provides several commands to undo changes you've made. It's important to understand the different ways to undo changes depending on your situation.

**Unstage files**
If you have staged a file using `git add` but decide you don't want to include it in your next commit, you can unstage it using `git restore --staged`.

```bash
git restore --staged <file>
```
Replace `<file>` with the name of the file you want to unstage. This command removes the file from the staging area, but leaves your changes in the working directory.

**Discard changes in working directory**
If you want to discard changes you've made in your working directory and revert a file back to the last committed version, you can use `git restore`.

```bash
git restore <file>
```
**Warning:** This command will overwrite the current changes in your working directory with the version from the last commit. Make sure you want to discard your changes before using this command.

**Undo last commit (keeping changes staged)**
If you want to undo the last commit but keep the changes you made in the staging area, you can use `git reset --soft HEAD~1`.

```bash
git reset --soft HEAD~1
```
This command moves the branch pointer back to the commit before the last one, effectively undoing the last commit. The changes from the undone commit are preserved in the staging area, allowing you to modify them or create a new commit.

This guide covers the essential steps to get started with Git for version control. As you continue to use Git, you'll discover more powerful features and workflows. Make sure to explore the other sections of this guide to deepen your understanding and skills.
