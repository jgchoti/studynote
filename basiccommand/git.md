# Guide to using git and GitHub

<details>
  <summary><h2>GitHub and Committing Changes</h2></summary>

When you commit changes in Git, it's like saving your game. But to share it or collaborate with others, you use a website called [GitHub](http://www.github.com).

**Create Repository (Folder)**: Before saving your work, create a new space on GitHub called a repository. Think of it like a folder for your project.

**Commit Changes (Save Game)**: Make changes to your project, and when you're ready to save them, commit those changes. It's like saving your game progress.

**Push to GitHub (Share your Saved Game)**: To share your progress with others or save it online, you push (upload) your committed changes to GitHub. This way, others can see what you've done, and you have a backup online.

In short, GitHub is where you store your project, commit is like saving changes, and pushing is like sharing or backing up your work online. 🚀

</details>

<details>
  <summary><h2>GitHub Setup Steps</h2></summary>

- **Initialize Git**: Run git init to initialize a new Git repository.
- **Add Remote Origin**: Use `git remote add origin <SSH link>` to link your local repository to a remote GitHub repository.
- **Add Changes**: Use `git add .` to stage all changes for commit.
- **Commit Changes**: Run `git commit -m "Add existing project files to Git"` to commit the staged changes.
- **Add Remote Origin (Optional)**: If you haven't added the remote origin earlier, you can do so now with `git remote add origin <SSH link>` to establish the connection to your GitHub repository.

  </details>

  <details>
  <summary><h2>Pull Request (PR)</h2></summary>
  When you've made changes to a branch and want them to be included in the main branch (typically 'main' or 'master') on GitHub, you create a Pull Request (PR). It's like leaving a note for the owner, asking them to check and merge your changes.
    
    The process is quite simple:
    
    1. You make a Pull Request on GitHub.
    2. The owner reviews your changes.
    3. If everything looks good, they click **“merge pull request”**.
    4. Your changes are then merged into the main branch.
    
  </details>
