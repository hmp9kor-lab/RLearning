# Learning Git

## 1. Introduction to Git

Git is a **version control system** that helps developers track changes in their code. It allows us to save different versions of a project, compare changes, fix mistakes, and work with other developers.

### Why do we use Git?
- Track changes made to files.
- Restore previous versions of code.
- Work on different features using branches.
- Collaborate with other developers.
- Upload and manage project code using GitHub.

## 2. Git vs GitHub

| Git | GitHub |
|---|---|
| A version control system. | An online platform for hosting Git repositories. |
| Works locally on your computer. | Helps teams share and collaborate on code. |
| Tracks file changes and versions. | Stores remote repositories and supports pull requests. |

## 3. Basic Git Workflow

```text
Working Directory
       ↓
   git add
       ↓
 Staging Area
       ↓
  git commit
       ↓
 Local Repository
       ↓
   git push
       ↓
 Remote Repository (GitHub)
```

- **Working Directory:** Where you create and modify files.
- **Staging Area:** Where you select changes to include in the next commit.
- **Commit:** A saved snapshot of your changes.
- **Remote Repository:** The online copy of your repository.

## 4. Important Git Commands

### 4.1 Check Git Installation

```bash
git --version
```

Displays the installed Git version.

### 4.2 Configure Your Identity

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

Git uses this information to identify who created each commit. Replace the example details with your own.

### 4.3 Initialize a Repository

```bash
git init
```

Initializes Git tracking in the current project folder.

### 4.4 Check File Status

```bash
git status
```

Shows which files are modified, staged, or untracked.

### 4.5 Stage Changes

```bash
git add filename.py
```

Stages a specific file.

```bash
git add .
```

Stages all changes in the current directory and its subdirectories, except files excluded by Git's ignore rules.

### 4.6 Commit Changes

```bash
git commit -m "Add initial project files"
```

Saves the staged changes as a commit with a descriptive message.

### 4.7 View Commit History

```bash
git log
```

Displays previous commits.

```bash
git log --oneline
```

Displays a shorter version of the commit history.

### 4.8 View Changes

```bash
git diff
```

Shows unstaged changes.

```bash
git diff --staged
```

Shows changes that are staged for the next commit.

## 5. Working with Branches

A branch allows you to work on a feature or fix without directly changing the main branch.

### Create a Branch

```bash
git branch feature-name
```

### Switch to a Branch

```bash
git switch feature-name
```

### Create and Switch in One Command

```bash
git switch -c feature-name
```

### List Branches

```bash
git branch
```

### Merge a Branch

First, switch to the branch that should receive the changes:

```bash
git switch main
git merge feature-name
```

Merge conflicts may occur if Git cannot automatically combine changes. Review and resolve them before completing the merge.

## 6. Connecting Git to GitHub

GitHub stores a remote copy of your repository.

### Add a Remote Repository

```bash
git remote add origin https://github.com/username/repository.git
```

Replace the URL with your actual GitHub repository URL.

### Verify the Remote

```bash
git remote -v
```

### Rename the Current Branch

```bash
git branch -M main
```

### Push Code to GitHub

```bash
git push -u origin main
```

The `-u` option sets the upstream branch, making future pushes from that branch easier.

## 7. Pulling and Fetching Changes

### Fetch Changes

```bash
git fetch origin
```

Downloads information about remote changes without merging them into your current branch.

### Pull Changes

```bash
git pull
```

Fetches remote changes and integrates them into the current branch according to the configured Git strategy.

## 8. Undoing Changes Safely

### Discard Unstaged Changes in a File

```bash
git restore filename.py
```

Discards unstaged changes in the specified file. These changes may be difficult or impossible to recover.

### Unstage a File

```bash
git restore --staged filename.py
```

Removes the file from the staging area without discarding its working-directory changes.

### Create a Reverting Commit

```bash
git revert COMMIT_ID
```

Creates a new commit that reverses the changes introduced by a specified commit.

**Important:** Be careful with commands such as `git reset --hard` and `git clean`, because they can permanently remove uncommitted work or untracked files.

## 9. Understanding the `.gitignore` File

The `.gitignore` file tells Git which untracked files and directories it should ignore.

Example:

```gitignore
# Python
__pycache__/
*.pyc
.venv/

# Node.js
node_modules/
dist/

# Environment variables and secrets
.env
.env.*

# IDE files
.vscode/
.idea/

# Log files
*.log
```

Files already tracked by Git are not automatically removed from tracking when you add them to `.gitignore`.

**Security tip:** Never commit API keys, passwords, access tokens, or other secrets to a repository.

## 10. A Typical Daily Git Workflow

When working on an existing project, a typical workflow is:

```bash
git status
git pull
# Make changes to your files
git diff
git add .
git status
git commit -m "Describe the changes"
git push
```

Before pulling or switching branches, make sure your local changes are safe. Follow your team's preferred branching and review process.

## 11. Common Git Problems

| Problem | Possible solution |
|---|---|
| Git is not recognized | Check whether Git is installed and available in the terminal PATH. |
| Nothing to commit | Check `git status` and ensure changes have been staged. |
| Push rejected | Fetch or pull remote changes and resolve any conflicts. |
| Authentication failed | Check your approved GitHub authentication method and repository permissions. |
| Merge conflict | Review conflicting files, resolve the conflicts, stage them, and complete the merge. |
| `.env` appears in Git | Check `.gitignore` and whether the file is already tracked. |

## 12. Practice Exercise

Create a small practice repository and perform these steps:

1. Create a folder named `git-practice`.
2. Open the folder in VS Code.
3. Run `git init`.
4. Create a file named `hello.txt`.
5. Add some text to the file.
6. Run `git status`.
7. Stage the file using `git add hello.txt`.
8. Commit it using `git commit -m "Add hello file"`.
9. Modify the file and inspect the changes using `git diff`.
10. Stage and commit the new changes.
11. Create a branch using `git switch -c practice-branch`.
12. Make another change and commit it.
13. Switch back to `main` and inspect the commit history using `git log --oneline --all`.

You can later connect this repository to GitHub to practise pushing and pulling changes.

## 13. Key Takeaways

- Git tracks changes and versions of project files.
- GitHub hosts repositories online and supports collaboration.
- `git add` stages changes.
- `git commit` saves a snapshot locally.
- `git push` sends commits to a remote repository.
- `git pull` retrieves and integrates remote changes.
- Branches help developers work on separate features.
- `.gitignore` helps keep unwanted files out of version control.
- Always review changes before committing or pushing code.

**Recommended learning order:** Start with `status`, `add`, `commit`, `log`, and `diff`. Then learn branches, merging, remote repositories, and conflict resolution.