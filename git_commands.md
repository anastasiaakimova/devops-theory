# How to use simple git commands (checkout, add, commit, push, reset)

| Command | Purpose | Examples |
|--------|---------|----------|
| **git checkout** | Used to switch branches or restore files | `git checkout main` — switch to existing branch<br>`git checkout -b feature-branch` — create and switch to new branch<br>`git checkout -- filename.txt` — restore file to last committed version |
| **git add** | Adds changes to the staging area before committing | `git add filename.txt` — add single file<br>`git add .` — add all changed files<br>`git add *.js` — add specific file types |
| **git commit** | Saves staged changes to the local repository | `git commit -m "Add new feature"` — basic commit<br>`git commit -a -m "Update multiple files"` — commit all tracked changes |
| **git push** | Sends local commits to a remote repository | `git push origin main` — push current branch<br>`git push -u origin feature-branch` — push new branch and set upstream |
| **git reset** | Undo changes (use with caution) | `git reset filename.txt` — unstage file<br>`git reset --soft HEAD~1` — undo last commit, keep changes<br>`git reset --hard HEAD~1` — undo last commit and discard changes |


# Advanced git usage (rewrite history, merge vs rebase)

| Topic / Command | Purpose | Description | Examples |
|----------------|---------|-------------|----------|
| **Rewrite history** | Modify existing commits | Rewriting commit history: changing commit messages, squashing commits, removing sensitive data, reordering commits | |
| git commit --amend | Change last commit | Used to change the most recent commit (message or content) | `git commit --amend -m "New commit message"` |
|  |  | Add new changes to the last commit | `git add <file>`<br>`git commit --amend` |
|  | ⚠️ Safety | Only safe if the commit has **not been pushed yet** | |
| **Interactive rebase** | Rewrite multiple commits | Used to modify commits that are farther back in history | |
| git rebase -i | Edit commit history | Allows you to stop at each commit to edit messages, add files, squash or reorder commits | `git rebase -i HEAD~3` |
|  |  | Rewrites commits by rebasing them onto the same base commit | |
|  | Use cases | Fix commit messages, squash multiple commits, remove sensitive information | |
| **Reset vs Revert** | Undo commits | Two different ways to undo changes | |
| git reset | Move HEAD | Moves HEAD to another commit (rewrites history) | `git reset --hard HEAD~1` |
|  | ⚠️ Dangerous | Dangerous if commits were already pushed | |
| git revert | Undo safely | Creates a new commit that undoes changes without rewriting history | `git revert <commit_hash>` |
|  | ✅ Safe | Safe for public repositories | |
| **Merge vs Rebase** | Integrate branches | Two ways to integrate changes from one branch into another | |
| git merge | Merge branches | Preserves all commits and creates a separate merge commit | `git checkout main`<br>`git merge feature` |
|  | History | History remains tree-like with branches | |
| git rebase | Reapply commits | Takes commits from one branch and places them on top of another | `git checkout feature`<br>`git rebase main` |
|  | History | History becomes linear and clean | |
|  | ⚠️ Rule | Do not rebase branches that other people already use | |
| **Best practices** | Usage rules | Merge — safe for public branches<br>Rebase — for clean history on private branches | |


# Literature:

- https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History