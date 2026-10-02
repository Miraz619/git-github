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




# Pull Request (PR)

A Pull Request is a request to add changes from one branch into another branch.

For example:

```text
cli-feature
     ↓
Pull Request
     ↓
main
```

Instead of directly changing `main`, I can work on a feature branch and create a Pull Request.

## Create a Pull Request

After completing my work on a branch, I first push the changes:

```bash
git add .
git commit -m "Add new feature"
git push
```

Then on GitHub:

1. Open the repository.
2. Click **Compare & pull request**.
3. Select:

```text
base: main
compare: cli-feature
```

Here:

- `base: main` = branch where the changes will be added
- `compare: cli-feature` = branch containing my new changes

Then add a PR title and description and click:

```text
Create pull request
```

---

## Code Review

Before merging a Pull Request, another developer can review the code.

A reviewer checks things like:

- Does the code work correctly?
- Are there any bugs?
- Is the code easy to understand?
- Does it follow the team's coding style?
- Are there any unnecessary changes?

The reviewer can:

```text
Approve
```

or:

```text
Request changes
```

---

## Assign a Reviewer

When creating a Pull Request, I can assign a reviewer from the **Reviewers** section.

Usually the reviewer can be:

- Team Lead
- Senior Developer
- Another team member

The workflow becomes:

```text
Create PR
↓
Assign Reviewer
↓
Code Review
↓
Approve / Request Changes
↓
Merge
```

---

## If the Reviewer Requests Changes

If the reviewer finds a problem, I do not need to create another Pull Request.

I make the changes in the **same branch**.

Then:

```bash
git add .
git commit -m "Fix issues from code review"
git push
```

The existing Pull Request automatically updates with the new commit.

Then the reviewer can review the changes again.

```text
PR created
↓
Reviewer requests changes
↓
Fix the code
↓
Commit
↓
Push
↓
Existing PR updates automatically
↓
Reviewer reviews again
↓
Approve
```

---

## Merge the Pull Request

After the PR is reviewed and approved, an authorized developer can merge it into `main`.

On GitHub:

```text
Merge pull request
↓
Confirm merge
```

Whether I can merge the PR depends on my repository permissions and the team's branch protection rules.

In many teams:

```text
Developer creates PR
↓
Team Lead / Reviewer checks it
↓
Reviewer approves
↓
Authorized developer merges it
```

---

# Git Pull

After the Pull Request is merged on GitHub, the remote `main` branch has the latest code.

My local `main` may still have the old code.

First switch to `main`:

```bash
git switch main
```

Then:

```bash
git pull
```

`git pull` downloads the latest changes and updates my local branch.

Example:

```text
GitHub main:
A → B → C

Local main:
A → B
```

After:

```bash
git pull
```

Local `main` becomes:

```text
A → B → C
```

---

# Git Fetch vs Git Pull

## `git fetch`

```bash
git fetch
```

`git fetch` gets the latest information from the remote repository but does **not** change my current working files.

Simple meaning:

> Check what is new on GitHub without applying it to my current branch.

It is useful for discovering new remote branches and commits.

Example:

```bash
git fetch
git branch -r
```

---

## `git pull`

```bash
git pull
```

`git pull` gets the latest changes and updates my current local branch.

Simple difference:

```text
git fetch
= Get information about remote changes
= Don't change my current files

git pull
= Get remote changes
+ Update my current branch
```

---

# Pull Request Workflow

```text
Work on feature branch
↓
git add .
↓
git commit
↓
git push
↓
Create Pull Request
↓
Assign Reviewer
↓
Code Review
↓
Fix changes if needed
↓
Reviewer approves
↓
Merge into main
↓
git switch main
↓
git pull
```



```md
# Git and GitHub Using VS Code UI

VS Code provides a graphical interface for Git, so many Git tasks can be done without using terminal commands.

## Open Source Control

Open the Source Control panel from the left sidebar or use:

```text
Ctrl + Shift + G
```

The Source Control panel shows changed, staged, and untracked files.

This is similar to:

```bash
git status
```

---

## Stage Changes Using VS Code UI

After changing a file, it appears under:

```text
Changes
```

Click the `+` icon beside the file.

This is the same as:

```bash
git add file-name
```

After staging, the file moves to:

```text
Staged Changes
```

---

## Commit Using VS Code UI

After staging:

1. Write a commit message in the Source Control message box.
2. Click **Commit**.

This is similar to:

```bash
git commit -m "commit message"
```

---

## Push Using VS Code UI

After committing, VS Code may show:

```text
Push
```

or:

```text
Sync Changes
```

Click it to send the commit to GitHub.

This is similar to:

```bash
git push
```

Example:

```text
↑1
```

means there is 1 local commit that has not been pushed yet.

Example:

```text
↓2 ↑1
```

means:

```text
↓2 = 2 remote commits are not available locally
↑1 = 1 local commit has not been pushed
```

---

# Create a Branch Using VS Code UI

Click the current branch name from the bottom-left corner of VS Code.

Example:

```text
main
```

Then select:

```text
Create new branch...
```

Enter a branch name, for example:

```text
ui-feature
```

Choose `main` as the source branch if needed.

VS Code creates the branch and usually switches to it automatically.

---

## Publish the Branch

A newly created branch exists only locally at first.

VS Code may show:

```text
Publish Branch
```

Click it to publish the branch to GitHub.

This is similar to:

```bash
git push -u origin ui-feature
```

After publishing:

```text
Local branch:
ui-feature

Remote branch:
origin/ui-feature
```

---

## Work on the UI Branch

Example file:

```text
ui.js
```

Example code:

```js
console.log("This file was created using the VS Code Git UI");
```

Then use the VS Code UI workflow:

```text
Change file
↓
Click +
↓
Stage Changes
↓
Write commit message
↓
Commit
↓
Push / Sync Changes
```

---

# Switching Branches with Uncommitted Changes

Suppose the current branch is:

```text
ui-feature
```

and a new file is created:

```text
ui.js
```

but the file is not committed yet.

Then switch to another branch:

```bash
git switch another-feature
```

If Git allows the branch switch, the uncommitted file may still remain in the working directory.

If the file is then staged and committed while on `another-feature`:

```bash
git add ui.js
git commit -m "Add ui.js"
git push
```

the commit belongs to:

```text
another-feature
```

not:

```text
ui-feature
```

## Important Rule

The commit belongs to the branch that is active when the commit is created.

Example:

```text
Create ui.js on ui-feature
↓
Do not commit
↓
Switch to another-feature
↓
git add
↓
git commit
↓
Commit belongs to another-feature
```

Git may prevent switching branches if the uncommitted changes conflict with files in the target branch.

Before switching branches, check:

```bash
git status
```

This helps confirm whether there are any uncommitted changes.
```