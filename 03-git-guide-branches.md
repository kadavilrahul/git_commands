# Git Guide for Beginners - Collaborating with Branches

This section introduces branching for parallel development and collaboration, enabling teams to work on features or fixes independently without disrupting the main codebase.

### Create New Branch

Create and switch to a new branch.

```bash
git checkout -b <new-branch-name>
```


### Switch Between Branches

Switch to an existing branch.

```bash
git checkout <branch-name>
```


### List Branches

List branches.

```bash
git branch
```
List local and remote branches:

```bash
git branch -a
```

### Push New Branch to Remote

Upload a new local branch to the remote repository.

```bash
git push --set-upstream origin <branch-name>
```

### Push the first change 

```bash
git push origin <branch-name>
```

### Merge a Branch

Integrate changes from another branch into the current branch.  Usually, you merge feature branches into your main branch.

```bash
git merge <branch-name>
```

### Delete a Branch

Delete a local branch.

```bash
git branch -d <branch-name>
```

Delete a remote branch.

```bash
git push origin --delete <branch-name>
```
