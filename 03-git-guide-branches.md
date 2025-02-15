# Git Guide for Beginners - Collaborating with Branches

This section introduces branching for parallel development and collaboration, enabling teams to work on features or fixes independently without disrupting the main codebase.

### Create New Branch

Create and switch to a new branch.

```bash
git checkout -b <new-branch-name>
```

*   **`git checkout -b <new-branch-name>`**: Create a new branch named `<new-branch-name>` and switch to it (e.g., `feature-x`, `fix-y`). Choose descriptive names for your branches.

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

### Merge a Branch

Integrate changes from another branch into the current branch.  Usually, you merge feature branches into your main branch.

```bash
git merge <branch-name>
```

*   **`git merge <branch-name>`**: Merge branch `<branch-name>` into the current branch.  Make sure you are on the branch that should receive the changes (e.g., `main` when merging a feature branch).

### Delete a Branch

Delete a local branch.

```bash
git branch -d <branch-name>
```

*   **`git branch -d <branch-name>`**: Delete local branch `<branch-name>`. Use `-D` instead of `-d` to force delete a branch that has not been merged.

Delete a remote branch.

```bash
git push origin --delete <branch-name>
```

*   **`git push origin --delete <branch-name>`**: Delete remote branch `<branch-name>`.
