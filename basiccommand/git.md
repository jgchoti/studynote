# Guide to using git and GitHub

- [Guide to using git and GitHub](#guide-to-using-git-and-github)
  - [Git Commands Cheat Sheet](#git-commands-cheat-sheet)
  - [GitHub and Committing Changes](#github-and-committing-changes)
  - [GitHub Setup Steps](#github-setup-steps)
  - [Pull Request (PR)](#pull-request-pr)
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

## GitHub and Committing Changes

When you commit changes in Git, it's like saving your game. But to share it or collaborate with others, you use a website called [GitHub](http://www.github.com).

**Create Repository (Folder)**: Before saving your work, create a new space on GitHub called a repository. Think of it like a folder for your project.

**Commit Changes (Save Game)**: Make changes to your project, and when you're ready to save them, commit those changes. It's like saving your game progress.

**Push to GitHub (Share your Saved Game)**: To share your progress with others or save it online, you push (upload) your committed changes to GitHub. This way, others can see what you've done, and you have a backup online.

In short, GitHub is where you store your project, commit is like saving changes, and pushing is like sharing or backing up your work online. 🚀

## GitHub Setup Steps

- **Initialize Git**: Run git init to initialize a new Git repository.
- **Add Remote Origin**: Use `git remote add origin <SSH link>` to link your local repository to a remote GitHub repository.
- **Add Changes**: Use `git add .` to stage all changes for commit.
- **Commit Changes**: Run `git commit -m "Add existing project files to Git"` to commit the staged changes.
- **Add Remote Origin (Optional)**: If you haven't added the remote origin earlier, you can do so now with `git remote add origin <SSH link>` to establish the connection to your GitHub repository.

## Pull Request (PR)

When you've made changes to a branch and want them to be included in the main branch (typically 'main' or 'master') on GitHub, you create a Pull Request (PR). It's like leaving a note for the owner, asking them to check and merge your changes.

1. You make a Pull Request on GitHub.
2. The owner reviews your changes.
3. If everything looks good, they click **“merge pull request”**.
4. Your changes are then merged into the main branch.

## Resolve Merge Conflict

1. `git checkout <your-branch-name>`
2. `git fetch --all`
3. `git merge main`
4. Resolve Conflicts:
   1. Open the conflicted file(s) in your code editor.
   2. Locate and resolve the conflict markers (<<<<<<<, =======, >>>>>>>).
   3. Decide which changes to keep and which to discard.
5. `git add <conflicted-file>`
6. `git commit -m "Resolve merge conflict"`
7. `git push origin <your-branch-name>`
