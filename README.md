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



# Git Branching

A branch is a separate line of development.

It allows us to work on a new feature without directly changing the `main` branch.

## Check Branches

```bash
git branch
```

Example:

```text
* main
  feature-test
```

The `*` shows the branch I am currently using.

## Create a Branch from GitHub

First, I created a branch named:

```text
feature-test
```

from GitHub.

Then I fetched the latest remote branches:

```bash
git fetch
```

To check remote branches:

```bash
git branch -r
```

Then I switched to the branch:

```bash
git switch feature-test
```

## Work on the Branch

I created a JavaScript file:

```bash
touch feature.js
```

Then I added, committed, and pushed it:

```bash
git add feature.js
git commit -m "Add feature JavaScript file"
git push
```

## Create a Branch from CLI

First, switch to `main`:

```bash
git switch main
```

Create a new branch:

```bash
git branch cli-feature
```

Then switch to it:

```bash
git switch cli-feature
```

## Important Branch Concept

When a new branch is created from `main`, it initially contains the same files and commit history as `main`.

Example:

```text
main
├── index.js
└── README.md

cli-feature
├── index.js
└── README.md
```

After creating the branch, new changes can be made separately inside `cli-feature`.

## Push a Locally Created Branch

After making changes:

```bash
git add .
git commit -m "Add CLI feature"
```

For the first push:

```bash
git push -u origin cli-feature
```

After that, I can simply use:

```bash
git push
```

## Branch Workflow

```text
main
↓
create branch
↓
switch to branch
↓
make changes
↓
git add
↓
git commit
↓
git push
```