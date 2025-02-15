# Git Guide for Beginners - More Useful Git Features

This section covers some additional helpful Git commands.

### Stash Changes Temporarily

Temporarily save uncommitted changes.

```bash
git stash
```

*   **`git stash`**: Save uncommitted changes.

**Create a named stash:**
```bash
git stash push -m "Your stash name"
```
*   **`git stash push -m "Your stash name"`**: Save uncommitted changes with a name.

**Stash untracked files as well:**
```bash
git stash -u
```
*   **`git stash -u`**:  Stash also untracked files.

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

**Apply a specific stash:**
```bash
git stash apply stash@{2}
```
*   **`git stash apply stash@{2}`**: Apply a specific stash from the list. Use `git stash list` to find the stash ID (e.g., `stash@{2}`).

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

**Show only the changes made in a commit:**
```bash
git show <commit-hash> --stat
```
*   **`git show <commit-hash> --stat`**: Show commit details and the summary of changes.

**Show changes to a specific file in a commit:**
```bash
git show <commit-hash>:<file-path>
```
*   **`git show <commit-hash>:<file-path>`**: Show the content of a specific file at the time of the commit.

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

**List all tags:**
```bash
git tag
```
*   **`git tag`**: List all tags.

**Delete a local tag:**
```bash
git tag -d <tag-name>
```
*   **`git tag -d <tag-name>`**: Delete a tag locally.

**Delete a remote tag:**
```bash
git push origin --delete <tag-name>
```
*   **`git push origin --delete <tag-name>`**: Delete a tag on the remote repository.

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

**Cache credentials temporarily (e.g., for 15 minutes):**
```bash
git config --global credential.helper cache
git config --global credential.helper 'cache --timeout=900'
```
*   **`git config --global credential.helper cache`**: Enable credential caching.
*   **`git config --global credential.helper 'cache --timeout=900'`**: Set the cache timeout to 900 seconds (15 minutes). Adjust the timeout as needed.

---

## Additional Useful Git Commands

### Undoing Changes

Commands to safely undo changes.

**Undo changes in the working directory (discard unstaged changes):**
```bash
git restore <file>
```
*   **`git restore <file>`**: Discard changes in the working directory for a specific file, reverting it to the last committed version.

**Undo changes in the staging area (unstage a file):**
```bash
git restore --staged <file>
```
*   **`git restore --staged <file>`**: Remove a file from the staging area, keeping the changes in the working directory.

### Reflog for Recovery

Using reflog to recover lost commits.

**View the reflog (history of HEAD changes):**
```bash
git reflog
```
*   **`git reflog`**: Display the reflog, which shows a history of all changes to the HEAD pointer, including branch creations, resets, and commits.

**Reset to a previous state using reflog:**
```bash
git reset --hard <reflog-hash>
```
*   **`git reset --hard <reflog-hash>`**: Reset your branch to a specific point in history using a reflog entry hash. Be cautious as this will discard commits after the specified point.

### Squashing Commits

Combine multiple commits into a single commit using interactive rebase.

**Start an interactive rebase for the last 3 commits:**
```bash
git rebase -i HEAD~3
```
*   **`git rebase -i HEAD~3`**: Initiate an interactive rebase session for the last 3 commits. You can adjust the number of commits as needed (e.g., `HEAD~5` for the last 5 commits).

During the interactive rebase, an editor will open. To squash commits:
*   Change `pick` to `squash` (or `s`) for the commits you want to combine into the previous commit.
*   The first `pick` line should remain as `pick`.
*   Save and close the editor. Git will then perform the rebase and allow you to edit the commit message for the squashed commit.

### Working with Logs

Advanced options for viewing commit history.

**Show a graph of commits:**
```bash
git log --graph --oneline --all --decorate
```
*   **`git log --graph --oneline --all --decorate`**: Display a graphical representation of the commit history, showing branches and merges in a compact one-line format. `--all` shows all branches, and `--decorate` adds branch and tag names.

**Show commits by a specific author:**
```bash
git log --author="Author Name"
```
*   **`git log --author="Author Name"`**: Filter and display commits made only by the specified author.

**Show commits affecting a specific file:**
```bash
git log -- <file-path>
```
*   **`git log -- <file-path>`**: Show the commit history that includes modifications to a specific file.

### Cleaning Up

Commands for removing unnecessary files and cleaning the repository.

**Remove untracked files (dry run - see what would be removed):**
```bash
git clean -n
```
*   **`git clean -n`**: Perform a dry run of the `git clean` command. It will show you which untracked files and directories would be removed without actually deleting them.

**Remove untracked files (actually remove files):**
```bash
git clean -f
```
*   **`git clean -f`**: Remove untracked files from the working directory. Be careful, as this action is irreversible.

**Remove untracked files and directories:**
```bash
git clean -fd
```
*   **`git clean -fd`**: Remove both untracked files and directories. Use with caution.

### Cherry-picking

Apply specific commits from one branch to another.

**Apply a specific commit to the current branch:**
```bash
git cherry-pick <commit-hash>
```
*   **`git cherry-pick <commit-hash>`**: Apply the changes introduced by a specific commit to the current branch.

**Cherry-pick multiple commits:**
```bash
git cherry-pick <commit1-hash> <commit2-hash>
```
*   **`git cherry-pick <commit1-hash> <commit2-hash>`**: Apply a range of specific commits to the current branch.

### Bisect for Debugging

Using binary search to find the commit that introduced a bug.

**Start a bisect session:**
```bash
git bisect start
```
*   **`git bisect start`**: Begin a bisect session to find a commit that introduced a regression.

**Mark the current commit as bad (containing the bug):**
```bash
git bisect bad
```
*   **`git bisect bad`**: Mark the currently checked out commit as "bad" because it contains the bug you are investigating.

**Mark a known good commit (not containing the bug):**
```bash
git bisect good <commit-hash>
```
*   **`git bisect good <commit-hash>`**: Mark a commit that is known to be "good" (i.e., it does not contain the bug).

Git will then automatically check out a commit in between the good and bad commits. Test this commit and mark it as either `git bisect good` or `git bisect bad`. Repeat this process until Git identifies the specific commit that introduced the bug.

**End the bisect session:**
```bash
git bisect reset
```
*   **`git bisect reset`**: Terminate the bisect session and return to the original branch.

### Aliases for Efficiency

Create shortcuts for frequently used Git commands.

**Shorten common commands (status, checkout, branch, commit):**
```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
```
*   **`git config --global alias.st status`**: Create an alias `st` for `status`. Now you can use `git st` instead of `git status`.
*   **`git config --global alias.co checkout`**: Create an alias `co` for `checkout`.
*   **`git config --global alias.br branch`**: Create an alias `br` for `branch`.
*   **`git config --global alias.ci commit`**: Create an alias `ci` for `commit`.

**Create a custom alias for a log graph:**
```bash
git config --global alias.lg "log --graph --oneline --all --decorate"
```
*   **`git config --global alias.lg "log --graph --oneline --all --decorate"`**: Create a custom alias `lg` for the detailed log graph command. Now you can use `git lg`.

---

## Best Practices

### Regular Cleanup

Keep your repository organized by regularly cleaning up old branches and stashes.
*   **Delete old branches**: Regularly delete branches that are merged and no longer needed to keep your repository clean and easier to navigate. `git branch -d <branch-name>` or `git branch -D <branch-name>` (for forced deletion).
*   **Manage stashes**: Review your stashes periodically using `git stash list`. Apply or drop stashes that are no longer necessary to avoid clutter.

### Commit Messages

Write clear and descriptive commit messages.
*   **Use imperative mood**: Start your commit message with an imperative verb (e.g., "Fix", "Add", "Update") in the subject line.
*   **Be concise in the subject**: Keep the subject line short and to the point (under 50 characters).
*   **Provide details in the body**: If necessary, add a more detailed explanation in the body of the commit message, separated from the subject by a blank line. Explain the *why* and *what* of the change.

**Example of a good commit message:**
```
Fix login issue by updating authentication logic

This commit resolves the login problem reported by users.
The authentication logic was updated to correctly handle expired sessions and improve security.
```
```bash
git commit -m "Fix login issue by updating authentication logic"
```

### Backup Tags

Tag important commits before making risky changes, such as rebasing or major refactoring.
```bash
git tag backup-before-rebase
```
*   **`git tag backup-before-rebase`**: Create a tag named `backup-before-rebase` on the current commit. This tag serves as a backup point in case something goes wrong during the risky operation.

---

## Advanced Features

### Interactive Staging

Stage parts of a file interactively.

**Interactively stage changes:**
```bash
git add -p
```
*   **`git add -p`**: Start an interactive staging session. Git will present changes in chunks and ask if you want to stage each chunk. You can choose to stage, not stage, split chunks further, or edit chunks.

### Sparse Checkout

Work with a subset of files in large repositories.

**Enable sparse checkout:**
```bash
git sparse-checkout init
```
*   **`git sparse-checkout init`**: Enable sparse checkout in your repository. This prepares your repository to only checkout a subset of files.

**Specify directories or files to include:**
```bash
git sparse-checkout set <directory-or-file>
```
*   **`git sparse-checkout set <directory-or-file>`**: Define the directories or files you want to include in your sparse checkout. For example, `git sparse-checkout set docs src/module1`.

### Worktrees

Work on multiple branches simultaneously without switching directories.

**Create a new worktree for a branch:**
```bash
git worktree add ../branch-folder <branch-name>
```
*   **`git worktree add ../branch-folder <branch-name>`**: Create a new worktree linked to the branch `<branch-name>`. The worktree will be created in a new directory `../branch-folder`. You can now work on this branch in the new directory while keeping your original working directory intact.

This expanded guide provides a more comprehensive overview of useful Git features, best practices, and advanced techniques.
