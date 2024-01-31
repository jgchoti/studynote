# Guide to using git and GitHub

- [Guide to using git and GitHub](#guide-to-using-git-and-github)
  - [Git Commands Cheat Sheet](#git-commands-cheat-sheet)
  - [Resolve Merge Conflict](#resolve-merge-conflict)

## Git Commands Cheat Sheet

- **Start Project:**

  - `git init`: Begin a new project.

- **Save Changes:**

  - `git add .`: Save all changes.
  - `git add index.html`: Save specific changes.

- **Record Changes:**

  - `git commit -m "Add existing file"`: Describe and save changes.

- **Check Status:**

  - `git status`: See what's happening.

- **Review History:**

  - `git log`: Check project history.
  - `git log --oneline`: View a simplified commit log in one line.

- **Navigate Time:**

  - `git checkout <# of commit>`: Go back in time.

- **Connect to GitHub:**

  - `git remote add origin [repo link]`: Connect to GitHub.
  - `git fetch --all`: Fetch all changes from all remotes.

- **Send Changes to GitHub:**

  - `git push -u origin master`: Share changes on GitHub (master).
  - `git push -u origin <branchname>`: Share changes on a branch.

- **Create & Manage Branches:**

  - `git checkout -b <name of branch>`: Create a new branch.
  - `git branch`: See all branches.

- **Stay Updated:**

  - `git pull origin master`: Get the latest changes from GitHub.

- **Fix Conflicts Locally:**

  - `git merge main`: Resolve local conflicts.

- **Update with Main on GitHub:**

  - `git merge origin main`: Stay current with GitHub changes.

## Resolve Merge Conflict

1. `git checkout <your-branch-name>``
2. `git fetch --all`
3. `git merge main`
4. Resolve Conflicts:
   1. Open the conflicted file(s) in your code editor.
   2. Locate and resolve the conflict markers (<<<<<<<, =======, >>>>>>>).
   3. Decide which changes to keep and which to discard.
5. `git add <conflicted-file>`
6. `git commit -m "Resolve merge conflict"`
7. `git push origin <your-branch-name>`
