```markdown
# Git Setup and Usage Guide

This guide provides step-by-step instructions for installing, configuring, and using Git. All commands are formatted for easy copying and use in a GitHub repository.

---

## Install Git

To install Git on your system, use the following commands:

```bash
sudo apt update
sudo apt install git
git --version
```

---

## Configure Git

### Initialize Git
To initialize a Git repository in your directory:

```bash
git init
```

Check if the directory is a Git repository:

```bash
git rev-parse --is-inside-work-tree
```

### Set Up User Information
Set your username and email address to associate commits with your GitHub account:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

Verify the configuration:

```bash
git config --global --list
```

### Store GitHub Token Using Credential Manager
To store your GitHub token securely:

```bash
git config --global credential.helper manager-core
```

When pushing for the first time, Git will prompt for:
- **Username**: Your GitHub username
- **Password**: Use your Personal Access Token instead of a password.

### Add Remote Repository
Add the remote URL for your GitHub repository:

```bash
git remote add origin https://github.com/username/repository_name.git
```

Verify the remote URL:

```bash
git remote -v
```

---

## Basic Git Workflow

### Check Status
To check the status of your repository:

```bash
git status
```

### Stage and Commit Changes
Stage all files:

```bash
git add .
```

Commit the changes with a message:

```bash
git commit -m "Initial commit"
```

### Push Changes
Push the changes to the remote repository:

```bash
git push --set-upstream origin master
```

---

## Clone a Repository

To clone a repository:

```bash
git clone https://github.com/username/repository_name.git
cd repository_name
```

---

## Clone a Specific Commit

To clone a repository and check out a specific commit:

```bash
git clone <repository-url>
cd <repository-name>
git checkout <commit-hash>
```

---

## Other Git Commands

### Set Upstream Branch
To set the upstream branch:

```bash
git branch --set-upstream-to=origin/master master
```

### Create or Switch Branches
List all branches:

```bash
git branch
```

Switch to another branch:

```bash
git checkout <branch-name>
```

Create and switch to a new branch:

```bash
git checkout -b <new-branch-name>
```

### Pull Changes
To pull changes from the remote repository:

```bash
git pull origin <branch-name>
```

For the main branch:

```bash
git pull origin main
```

### Update Repository in a Single Command
For Linux:

```bash
git add . && git commit -m "Update" && git push
```

For Windows:

```bash
git add . ; git commit -m "Update" ; git push
```

---

## View Commit History

To view all commits:

```bash
git log
```

For a simplified view:

```bash
git log --oneline
```

To view all commits with branches and tags:

```bash
git log --oneline --decorate --all --graph
```

---

## Stash Changes

To temporarily save uncommitted changes:

```bash
git stash
```

List all stashes:

```bash
git stash list
```

Apply the most recent stash:

```bash
git stash apply
```

Remove the most recent stash:

```bash
git stash drop
```

Clear all stashes:

```bash
git stash clear
```

---

## Reset to a Specific Commit

To hard reset to a specific commit:

```bash
git reset --hard <commit-hash>
git push --force
```

⚠️ **Warning**: This will erase all commits after the specified commit.

---

## Tag Management

### Create Tags
Create a lightweight tag:

```bash
git tag <tag-name>
```

Create an annotated tag:

```bash
git tag -a <tag-name> -m "Tag message"
```

### Push Tags
Push a specific tag:

```bash
git push origin <tag-name>
```

Push all tags:

```bash
git push origin --tags
```

### Delete Tags
Delete a tag locally:

```bash
git tag -d <tag-name>
```

Delete a tag remotely:

```bash
git push origin --delete <tag-name>
```

---

## Push from a New Branch

To push changes from a new branch:

```bash
git push --set-upstream origin <branch-name>
```

---

## Additional Commands

- View all branches (local and remote):

  ```bash
  git branch -a
  ```

- Remove files from Git tracking but keep them locally:

  ```bash
  git rm --cached <file-pattern>
  ```

- View a specific commit:

  ```bash
  git show <commit-hash>
  ```

- View all commits with date and time:

  ```bash
  git log --oneline --pretty=format:"%h %ad %s" --date=format:"%Y-%m-%d %H:%M:%S"
  ```

---

## Download Git

To download Git, visit the official website: [https://git-scm.com/downloads](https://git-scm.com/downloads).

For Windows:
1. Download the installer.
2. Run the installer and follow the setup instructions.
3. Select "Git from the command line and also from 3rd-party software" during installation.

---

This guide provides a comprehensive overview of Git commands and workflows for managing repositories effectively.
```