# Git Guide for Beginners - Collaborating with Branches

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
