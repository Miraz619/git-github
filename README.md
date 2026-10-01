# Git & GitHub Learning Notes

This repository contains my practice while learning Git and GitHub.

## What I Have Learned So Far

### 1. Open a Project Folder in VS Code

```bash
code .
```

`code .` opens the current folder in VS Code.

### 2. Initialize Git

```bash
git init
```

This initializes Git inside the project.

### 3. Check Git Status

```bash
git status
```

This shows the current state of the repository, including untracked, modified, and staged files.

### 4. Add Files to Staging

```bash
git add .
```

This adds all changed files to the staging area.

### 5. Create a Commit

```bash
git commit -m "Initial commit"
```

A commit saves a snapshot of the current changes in Git history.

### 6. Rename the Branch to `main`

```bash
git branch -M main
```

This renames the current branch to `main`.

### 7. Connect the Local Repository to GitHub

```bash
git remote add origin <repository-url>
```

This connects the local Git repository to a GitHub repository.

### 8. Check the Remote Repository

```bash
git remote -v
```

This shows which remote repository is connected to the local project.

### 9. Push Code to GitHub

```bash
git push -u origin main
```

This pushes the local `main` branch to GitHub.

After the first push, I can usually use:

```bash
git push
```

## Basic Git Workflow

```text
Change code
↓
git status
↓
git add .
↓
git commit -m "message"
↓
git push
```