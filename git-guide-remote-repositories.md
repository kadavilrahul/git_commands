# Git Guide for Beginners - Working with Remote Repositories

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
