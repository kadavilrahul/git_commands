# Git Guide for Beginners

This guide will help you get started with Git, a powerful tool for tracking changes in your code and collaborating with others. Think of Git as a way to save different versions of your project, so you can always go back to an earlier version if you make a mistake or want to try something new. It's also essential for working with others on projects, especially on platforms like GitHub.

Let's go through the basics step-by-step.

## Install Git

First, you need to install Git on your computer.  Follow these commands for Linux (if you're using Windows or macOS, you can download Git from the official website [https://git-scm.com/downloads](https://git-scm.com/downloads) and follow the installation instructions).

```bash
sudo apt update
sudo apt install git
git --version
```

*   **`sudo apt update`**: This command updates the list of available software on your Linux system. It's a good practice to run this before installing new software.
*   **`sudo apt install git`**: This command installs Git on your system. You'll be asked for your password to confirm the installation.
*   **`git --version`**: After installation, this command checks if Git is installed correctly and shows you the version of Git you have installed.

## Configure Git - Setting Up Your Identity

Before you start using Git, you need to tell Git who you are. This is important because every change you save (called a "commit") will be marked with your name and email.

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

*   **`git config --global user.name "Your Name"`**:  Replace `"Your Name"` with your actual name. This command sets your name for all Git projects on your computer.
*   **`git config --global user.email "your.email@example.com"`**: Replace `"your.email@example.com"` with your email address. Use the email address associated with your GitHub account if you plan to use GitHub.

You can check your configuration with:

```bash
git config --global --list
```

This command will show you a list of all your Git configurations.

## Basic Git Workflow - Your First Project

Let's walk through the basic steps of using Git in a project.

### 1. Initialize a Git Repository

To start using Git in your project, you need to turn your project folder into a Git repository.  Go to your project folder in the terminal and run:

```bash
git init
```

*   **`git init`**: This command initializes a new Git repository in the current folder. It creates a hidden folder called `.git` which Git uses to track changes. You only need to run this command once per project.

You can check if a folder is a Git repository by running:

```bash
git rev-parse --is-inside-work-tree
```

If it's a Git repository, it will output `true`.

### 2. Check the Status of Your Project

To see what's going on in your project and what Git is tracking, use the `status` command:

```bash
git status
```

*   **`git status`**: This command shows you the current state of your repository. It tells you about:
    *   **Untracked files**: Files that Git doesn't know about yet.
    *   **Changes not staged for commit**: Files that Git knows about and you've changed, but haven't prepared to save yet.
    *   **Changes to be committed**: Files that you've prepared to save (staged).
    *   The current branch you are working on (we'll talk about branches later).

### 3. Stage Your Changes

When you make changes to your files, Git needs to know which changes you want to save in your next version (commit).  "Staging" is the process of selecting changes you want to include in your next save.

To stage all changed files, use:

```bash
git add .
```

*   **`git add .`**: This command stages all changes in the current directory and its subdirectories.  The `.` means "current directory".  You can also stage specific files by using `git add <filename>`.

After staging, if you run `git status` again, you'll see the changes are now "Changes to be committed".

### 4. Commit Your Changes - Save Your Progress

Once you've staged your changes, you can "commit" them. A commit is like a snapshot of your project at a specific point in time.  It's a saved version of your work.

```bash
git commit -m "Your commit message"
```

*   **`git commit -m "Your commit message"`**: This command saves your staged changes as a new commit.
    *   **`-m "Your commit message"`**:  The `-m` flag lets you add a message to your commit.  **It's very important to write clear and concise commit messages** that describe what changes you made.  For example, "Fixing typo on homepage" or "Adding new feature: user login".

### 5. View Commit History

To see a history of all the commits you've made, you can use the `log` command:

```bash
git log
```

*   **`git log`**: This command displays a list of all commits in your repository, in reverse chronological order (newest first). It shows the commit hash (a unique ID), author, date, and commit message.

For a simpler view, use:

```bash
git log --oneline
```

*   **`git log --oneline`**: This shows each commit in a single line, with a shortened commit hash and the commit message.

## Working with Remote Repositories (like GitHub)

Git is very powerful when you want to share your code online and collaborate with others.  Platforms like GitHub, GitLab, and Bitbucket use Git.  Let's see how to connect your local Git repository to a remote repository on GitHub.

### 1. Add a Remote Repository

First, you need to tell your local Git repository about your remote repository on GitHub.  You'll need the URL of your repository from GitHub. It will look something like `https://github.com/username/repository_name.git`.

```bash
git remote add origin https://github.com/username/repository_name.git
```

*   **`git remote add origin https://github.com/username/repository_name.git`**: This command adds a remote repository named `origin` to your local Git repository.
    *   **`origin`**:  `origin` is just a common name for the main remote repository. You could name it something else, but `origin` is the standard.
    *   **`https://github.com/username/repository_name.git`**: Replace this with the actual URL of your repository on GitHub.

You can verify the remote URL with:

```bash
git remote -v
```

*   **`git remote -v`**: This command shows you the remote repositories that are configured for your local repository.  The `-v` option makes it "verbose" and shows you the URLs.

### 2. Push Your Changes to the Remote Repository

To upload your local commits to the remote repository on GitHub, you use the `push` command:

```bash
git push --set-upstream origin main
```

*   **`git push --set-upstream origin main`**: This command pushes your commits to the `main` branch of the `origin` remote repository.
    *   **`push`**:  This command uploads your local commits to the remote repository.
    *   **`--set-upstream origin main`**:  This part is needed the first time you push from a new local branch. It sets up a connection between your local `main` branch and the remote `origin/main` branch.  After the first time, you can usually just use `git push origin main` or even just `git push` in many cases.
    *   **`origin`**: The name of the remote repository we added earlier.
    *   **`main`**:  The name of the branch you are pushing to on the remote repository.  The main branch is often called `main` or `master`.

You might be asked to enter your GitHub username and Personal Access Token (PAT) or password when you push for the first time. **It's highly recommended to use a Personal Access Token instead of your password for security.** You can generate a PAT in your GitHub settings (Settings -> Developer settings -> Personal access tokens).

### 3. Clone a Repository - Downloading from GitHub

If you want to work on a project that's already on GitHub, you can "clone" it to your local computer. Cloning creates a copy of the remote repository on your machine.

```bash
git clone https://github.com/username/repository_name.git
cd repository_name
```

*   **`git clone https://github.com/username/repository_name.git`**: This command clones (downloads) the repository from the given URL to your current directory.
    *   **`https://github.com/username/repository_name.git`**: Replace this with the URL of the GitHub repository you want to clone.
*   **`cd repository_name`**: After cloning, Git will create a new folder with the repository name. This command changes your current directory to that new folder so you can start working on the project.

## Working with Branches

Branches are a powerful feature in Git that allow you to work on different features or fixes in isolation.  Think of branches as creating separate timelines of development.

### 1. Create a New Branch

To create a new branch and switch to it, use:

```bash
git checkout -b <new-branch-name>
```

*   **`git checkout -b <new-branch-name>`**: This command creates a new branch and immediately switches to it.
    *   **`checkout`**:  The `checkout` command is used to switch branches or commits.
    *   **`-b <new-branch-name>`**: The `-b` flag tells `checkout` to create a new branch named `<new-branch-name>` if it doesn't exist and then switch to it.  Replace `<new-branch-name>` with the name you want to give to your new branch (e.g., `feature-login`, `fix-bug-123`).

### 2. Switch Between Branches

To switch to an existing branch, use:

```bash
git checkout <branch-name>
```

*   **`git checkout <branch-name>`**: This command switches your working directory to the branch named `<branch-name>`. Replace `<branch-name>` with the name of the branch you want to switch to (e.g., `main`, `feature-login`).

### 3. List Branches

To see a list of all branches in your repository, use:

```bash
git branch
```

*   **`git branch`**: This command lists all branches in your local repository. The current branch you are on will be marked with an asterisk `*`.

To see both local and remote branches, use:

```bash
git branch -a
```

*   **`git branch -a`**: The `-a` flag shows "all" branches, including remote branches.

### 4. Push a New Branch to Remote

When you create a new branch locally, it's not automatically on the remote repository. To push your new branch to the remote repository, use:

```bash
git push --set-upstream origin <branch-name>
```

*   **`git push --set-upstream origin <branch-name>`**: This command pushes your local branch `<branch-name>` to the `origin` remote repository and sets up the remote tracking for this branch.  After the first push, you can usually just use `git push` when you are on this branch.

## Pulling Changes from Remote

When you are working with a remote repository, especially in a team, others might make changes and push them to the remote repository. To get those changes into your local repository, you need to "pull" them.

```bash
git pull origin <branch-name>
```

*   **`git pull origin <branch-name>`**: This command fetches changes from the `origin` remote repository and merges them into your current local branch.
    *   **`pull`**: This command downloads changes from a remote repository and tries to merge them into your current branch.
    *   **`origin`**: The name of the remote repository.
    *   **`<branch-name>`**: The name of the branch you want to pull from on the remote repository (e.g., `main`). If you are on the `main` branch and want to pull from `origin/main`, you can often just use `git pull origin main` or even just `git pull`.

For example, to pull changes from the `main` branch of the `origin` remote:

```bash
git pull origin main
```

## Other Useful Git Commands

Here are a few more Git commands that can be helpful:

### Stash Changes Temporarily

If you are working on something and need to switch to another branch quickly, but your current changes are not ready to be committed, you can use `git stash` to temporarily save your changes.

```bash
git stash
```

*   **`git stash`**: This command saves your uncommitted changes and reverts your working directory to the last commit. It's like putting your changes on a temporary shelf.

To see a list of your stashed changes:

```bash
git stash list
```

*   **`git stash list`**: This command shows you a list of all your stashes.

To bring back your most recent stashed changes:

```bash
git stash apply
```

*   **`git stash apply`**: This command applies the most recent stash to your working directory. Your stashed changes will be back, but they are still in the stash list.

To bring back your stashed changes and remove them from the stash list:

```bash
git stash pop
```

*   **`git stash pop`**: This command applies the most recent stash and then removes it from the stash list.

To remove a stash from the list:

```bash
git stash drop <stash-id>
```
*(You can find the `stash-id` from `git stash list`)*

To clear all stashes:

```bash
git stash clear
```

### View a Specific Commit

To see the details of a specific commit, you can use `git show` with the commit hash:

```bash
git show <commit-hash>
```

*   **`git show <commit-hash>`**: Replace `<commit-hash>` with the full or shortened hash of the commit you want to view. This will show you the commit message, author, date, and the changes made in that commit.

### Remove Files from Git Tracking (but keep them locally)

Sometimes you might want to stop tracking a file with Git (for example, a large file that shouldn't be in your repository), but you want to keep the file on your local computer. You can use `git rm --cached`:

```bash
git rm --cached <file-pattern>
```

*   **`git rm --cached <file-pattern>`**: This command removes files matching `<file-pattern>` from Git's tracking index, but leaves them in your working directory.  For example, `git rm --cached secrets.txt` will stop tracking `secrets.txt`.

### Tagging Commits

Tags are used to mark specific points in your commit history as important, usually for releases (like version 1.0, 2.0, etc.).

**Create a lightweight tag:**

```bash
git tag <tag-name>
```

**Create an annotated tag (recommended for releases):**

```bash
git tag -a <tag-name> -m "Tag message"
```

**Push tags to remote:**

```bash
git push origin --tags
```

## Credential Management - Storing Your GitHub Token Securely (Optional)

For more secure authentication with GitHub, especially when pushing, it's recommended to use a Personal Access Token (PAT) instead of your password.  You can configure Git to use a credential manager to store your token so you don't have to enter it every time.

```bash
git config --global credential.helper manager-core
```

*   **`git config --global credential.helper manager-core`**: This command configures Git to use the "manager-core" credential helper (Git Credential Manager Core), which can securely store your GitHub tokens.  You may need to install Git Credential Manager Core separately depending on your system.

When you push to GitHub for the first time after setting this up, Git will prompt you to log in through your web browser, which is a more secure way to authenticate.

## Conclusion

This guide has covered the basic Git commands and workflows to get you started. Git can seem a bit complex at first, but with practice, it will become an indispensable tool for your software development projects.  Keep experimenting with these commands and explore more advanced features as you become more comfortable. Happy coding!
