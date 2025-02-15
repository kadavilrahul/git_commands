# Git Guide for Beginners - More Useful Git Features

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
