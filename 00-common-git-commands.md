# Most Used Git Commands

This guide provides a quick reference for the most commonly used Git commands in day-to-day development.

## Quick Reference - Most Common Commands
```bash
# Repository Setup and Configuration
git clone https://github.com/username/repository.git    # Clone a repository
git clone https://github.com/username/repository.git .  # Clone a Git repository directly into the current directory (root) without creating a new folder
git clone -b <branch-name> <repository-url>             # Clone a specific branch of a Git repository
git init                                                # Initialize a new repository
git config --global user.name "Your Name"             # Set username globally
git config --global user.email "your@email.com"       # Set email globally
git config --global credential.helper store           # Store credentials

# Basic Operations
git add .                                             # Stage all changes
git commit -m "commit message"                        # Commit with message
git push                                             # Push to remote
git pull                                             # Pull from remote
git status                                           # Check repository status
git add . && git commit -m "Update" && git push      # Stage, commit, and push changes

# Branch Management
git branch                                           # List branches
git checkout -b branch-name                          # Create and switch to new branch
git checkout branch-name                             # Switch to existing branch
git push --set-upstream origin branch-name           # Push new branch to remote
git add . && git commit -m "Update"                  # Add and commit first changes
git push origin <branch-name>                        # Push the first change to remote
git branch -d branch-name                            # Delete local branch
git push origin --delete branch-name                 # Delete remote branch

# History and Logs
git log --oneline                                    # Compact history view
git log --pretty=format:"%h %ad %s" --date=format:"%Y-%m-%d %H:%M:%S"  # Formatted log
git log --oneline --decorate --all --graph          # Visual commit history

# Remote Operations
git remote -v                                        # List remote repositories
git remote add origin https://github.com/user/repo.git  # Add remote
git push -u origin main                              # Push and set upstream
git push -f origin main                              # Force push to main

# Reset and Clean
git reset --hard commit-hash                         # Reset to specific commit
git clean -f                                         # Remove untracked files
git stash                                            # Stash changes
```

## Basic Commands

### Getting Started
```bash
git init                    # Initialize a new Git repository
git clone <repository-url>  # Clone a remote repository
git config --global user.name "Your Name"    # Set your username
git config --global user.email "your@email.com"  # Set your email
```

### Basic Workflow
```bash
git status                  # Check the status of your working directory
git add <file>             # Stage a specific file
git add .                  # Stage all changes
git commit -m "message"    # Commit staged changes with a message
git push                   # Push commits to remote repository
git pull                   # Fetch and merge changes from remote repository
```

### Working with Branches
```bash
git branch                 # List all local branches
git branch <branch-name>   # Create a new branch
git checkout <branch-name> # Switch to a branch
git checkout -b <branch-name>  # Create and switch to a new branch
git merge <branch-name>    # Merge a branch into current branch
git branch -d <branch-name>    # Delete a branch
```

### Viewing Information
```bash
git log                    # View commit history
git log --oneline         # View commit history (compact)
git diff                  # View unstaged changes
git diff --staged         # View staged changes
git show <commit-id>      # View specific commit details
```

## Intermediate Commands

### Undoing Changes
```bash
git restore <file>         # Discard changes in working directory
git reset HEAD <file>      # Unstage changes
git reset --soft HEAD~1    # Undo last commit, keep changes staged
git reset --hard HEAD~1    # Undo last commit and all changes
git revert <commit-id>     # Create new commit that undoes specified commit
```

### Remote Repository
```bash
git remote -v              # List remote repositories
git remote add <name> <url>    # Add a remote repository
git fetch                  # Download objects from remote
git push -u origin <branch>    # Push and set upstream branch
git pull --rebase         # Pull changes and rebase local commits
```

### Stashing Changes
```bash
git stash                  # Temporarily store modified files
git stash list            # List all stashed changes
git stash pop             # Apply and remove latest stash
git stash apply           # Apply latest stash (keep it in stash)
git stash drop            # Remove latest stash
```

## Advanced Commands

### History and Comparison
```bash
git blame <file>          # Show who changed what and when in file
git log -p <file>         # Show commit logs and patches for file
git log --graph --oneline # Show commit history as graph
```

### Maintenance
```bash
git clean -n              # Show what files would be removed
git clean -f              # Remove untracked files
git gc                    # Clean unnecessary files and optimize local repository
```

## Tips

1. Always check your status with `git status` before making changes
2. Write meaningful commit messages
3. Pull before pushing to avoid conflicts
4. Create new branches for new features/fixes
5. Regularly push your changes to remote repository

## Best Practices

1. Commit related changes together
2. Commit often
3. Don't commit half-done work
4. Test before you commit
5. Write good commit messages
6. Use branches effectively
7. Agree on a workflow with your team

Remember: These commands cover most day-to-day Git operations. For more specific use cases, consult the official Git documentation or use `git help <command>` for detailed information about any command.
