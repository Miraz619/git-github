# Git & GitHub Learning Notes

This repository contains beginner-friendly notes and practice examples for learning Git and GitHub.

---

# Table of Contents

# Table of Contents

1. [Git Basics](#1-git-basics)
2. [Git Branching](#2-git-branching)
3. [Pull Requests](#3-pull-requests)
4. [Git Pull and Fetch](#4-git-pull-and-fetch)
5. [Git Using VS Code UI](#5-git-using-vs-code-ui)
6. [Git Reset](#6-git-reset)
7. [Git Stash](#7-git-stash)
8. [Git Bisect](#8-git-bisect)
9. [Quick Command Reference](#9-quick-command-reference)
10. [Git Diff](#10-git-diff)
11. [Git Log](#11-git-log)
12. [Git Ignore](#12-git-ignore)
13. [Merge Conflicts](#13-merge-conflicts)

---

# 1. Git Basics

## Open a Project in VS Code

```bash
code .
```

`code .` opens the current folder in VS Code.

---

## Initialize Git

```bash
git init
```

Starts Git inside the current project.

---

## Check Git Status

```bash
git status
```

Shows:

- Untracked files
- Modified files
- Staged files
- Current branch information

---

## Stage Changes

Stage all changes:

```bash
git add .
```

Stage one file:

```bash
git add filename
```

Staging means:

> The changes are selected and ready for the next commit.

Simple flow:

```text
Change file
↓
git add
↓
Staged
↓
git commit
```

---

## Create a Commit

```bash
git commit -m "Initial commit"
```

A commit saves a snapshot of the staged changes in Git history.

Simple idea:

```text
Changed
↓
Staged
↓
Committed
```

---

## Rename Branch to Main

```bash
git branch -M main
```

Renames the current branch to `main`.

---

## Connect Local Repository to GitHub

```bash
git remote add origin <repository-url>
```

Check the connected remote:

```bash
git remote -v
```

---

## Push to GitHub

First push:

```bash
git push -u origin main
```

After that:

```bash
git push
```

`-u` connects the local branch with the remote branch.

---

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

---

# 2. Git Branching

A branch is a separate line of development.

Branches allow new features or changes to be developed without directly changing `main`.

---

## Check Local Branches

```bash
git branch
```

Example:

```text
* main
  feature-test
```

The `*` shows the current branch.

---

## Check Remote Branches

```bash
git branch -r
```

Example:

```text
origin/main
origin/feature-test
```

---

## Create a Branch from GitHub

If a branch is created on GitHub, first get the latest remote information:

```bash
git fetch
```

Check remote branches:

```bash
git branch -r
```

Then switch to the branch:

```bash
git switch feature-test
```

Git can create a local tracking branch automatically when the remote branch exists.

---

## Create a Branch from CLI

First switch to the branch that should be the starting point:

```bash
git switch main
```

Create a branch:

```bash
git branch cli-feature
```

Switch to it:

```bash
git switch cli-feature
```

---

## Important Branch Concept

A new branch starts from the commit where it was created.

Example:

```text
main
├── index.js
└── README.md
```

After creating `cli-feature` from `main`:

```text
main
├── index.js
└── README.md

cli-feature
├── index.js
└── README.md
```

At first, both branches have the same files.

New changes can then be made separately.

---

## Push a New Local Branch

After making changes:

```bash
git add .
git commit -m "Add CLI feature"
```

First push:

```bash
git push -u origin cli-feature
```

After that:

```bash
git push
```

---

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

---

# 3. Pull Requests

A Pull Request (PR) is a request to merge changes from one branch into another.

Example:

```text
feature branch
↓
Pull Request
↓
Review
↓
Merge
↓
main
```

---

## Create a Pull Request

First push the feature branch:

```bash
git add .
git commit -m "Add new feature"
git push
```

On GitHub:

```text
base: main
compare: feature-branch
```

Meaning:

```text
base
= branch receiving the changes

compare
= branch containing the new changes
```

Then click:

```text
Create pull request
```

---

## Code Review

Before merging, another developer can review the code.

The reviewer may check:

- Does the code work?
- Are there bugs?
- Is the code understandable?
- Does it follow team standards?
- Are there unnecessary changes?

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

A reviewer may be:

- Team Lead
- Senior Developer
- Another team member

Workflow:

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

## If Changes Are Requested

There is usually no need to create a new PR.

Fix the code in the same branch:

```bash
git add .
git commit -m "Fix issues from code review"
git push
```

The existing Pull Request updates automatically.

Flow:

```text
PR created
↓
Reviewer requests changes
↓
Fix code
↓
Commit
↓
Push
↓
Same PR updates
↓
Review again
```

---

## Merge the Pull Request

After approval, an authorized developer can merge the PR.

```text
Merge pull request
↓
Confirm merge
```

Who can merge depends on repository permissions and branch protection rules.

---

# 4. Git Pull and Fetch

## Git Fetch

```bash
git fetch
```

`git fetch` gets the latest information from the remote repository.

It does **not** update the current working files.

Simple meaning:

```text
Check what changed on GitHub
but
do not apply the changes yet
```

Useful for:

- New remote branches
- New remote commits
- Updating remote information

---

## Git Pull

```bash
git pull
```

`git pull` gets remote changes and updates the current local branch.

Example:

```text
GitHub:
A → B → C

Local:
A → B
```

After:

```bash
git pull
```

Local becomes:

```text
A → B → C
```

---

## Fetch vs Pull

```text
git fetch
= get remote information
= current files stay unchanged

git pull
= get remote changes
+ update current branch
```

---

## After a Pull Request Is Merged

Switch to `main`:

```bash
git switch main
```

Then:

```bash
git pull
```

This updates the local `main` with the newly merged code.

---

# 5. Git Using VS Code UI

VS Code provides a graphical interface for Git.

Open Source Control:

```text
Ctrl + Shift + G
```

---

## Source Control Panel

The Source Control panel shows:

- Changed files
- Staged files
- Untracked files

This is similar to:

```bash
git status
```

---

## Stage Changes Using VS Code

Changed files appear under:

```text
Changes
```

Click the `+` icon beside a file.

This is similar to:

```bash
git add filename
```

The file moves to:

```text
Staged Changes
```

---

## Commit Using VS Code

After staging:

1. Write a commit message.
2. Click **Commit**.

This is similar to:

```bash
git commit -m "commit message"
```

---

## Push Using VS Code

VS Code may show:

```text
Push
```

or:

```text
Sync Changes
```

This is similar to:

```bash
git push
```

Example:

```text
↑1
```

Means:

```text
1 local commit has not been pushed
```

Example:

```text
↓2 ↑1
```

Means:

```text
↓2 = 2 remote commits are not local yet
↑1 = 1 local commit is not pushed yet
```

---

## Create a Branch Using VS Code UI

Click the current branch name in the bottom-left corner.

Example:

```text
main
```

Choose:

```text
Create new branch...
```

Enter:

```text
ui-feature
```

Choose `main` as the starting branch if needed.

VS Code usually creates and switches to the new branch automatically.

---

## Publish a Branch

A newly created branch initially exists only locally.

Click:

```text
Publish Branch
```

This is similar to:

```bash
git push -u origin ui-feature
```

After publishing:

```text
Local:
ui-feature

Remote:
origin/ui-feature
```

---

## Switching Branches with Uncommitted Changes

Suppose `ui.js` is created on:

```text
ui-feature
```

but it is not committed.

Then another branch is selected.

If Git allows the switch, the uncommitted change may remain in the working directory.

If the file is committed while on another branch:

```bash
git add ui.js
git commit -m "Add ui.js"
```

that commit belongs to the **current branch**.

Important rule:

> A commit belongs to the branch that is active when the commit is created.

Before switching branches:

```bash
git status
```

Check for unfinished changes.

---

# 6. Git Reset

`git reset` moves the current branch to another commit.

The reset mode controls what happens to:

1. Commit history
2. Staging area
3. Working files

---

## Three Reset Modes

| Mode | Commit Removed | Changes Staged | Changes Kept |
|---|---|---|---|
| `--soft` | Yes | Yes | Yes |
| `--mixed` | Yes | No | Yes |
| `--hard` | Yes | No | No for tracked changes |

Simple memory rule:

```text
soft  = keep changes staged
mixed = keep changes unstaged
hard  = discard tracked changes
```

---

## HEAD

`HEAD` means the current position in Git history.

Example:

```text
A → B → C
        ↑
       HEAD
```

One commit before HEAD:

```text
HEAD~1
```

Two commits before HEAD:

```text
HEAD~2
```

---

## Mixed Reset

```bash
git reset --mixed HEAD~1
```

or simply:

```bash
git reset HEAD~1
```

Meaning:

```text
Undo commit
Keep code
Unstage changes
```

Example:

```text
Before:
A → B → C

After:
A → B
```

Changes from C remain in the working directory.

---

## Soft Reset

```bash
git reset --soft HEAD~1
```

Meaning:

```text
Undo commit
Keep code
Keep changes staged
```

The changes are ready to commit again.

---

## Hard Reset

```bash
git reset --hard HEAD~1
```

Meaning:

```text
Undo commit
Discard tracked changes
```

This should be used carefully.

Important:

> `git reset --hard` normally does not remove untracked files.

---

## Reset a Specific Commit

Check history:

```bash
git log --oneline
```

Then:

```bash
git reset --mixed <commit-id>
```

or:

```bash
git reset --soft <commit-id>
```

or:

```bash
git reset --hard <commit-id>
```

---

## Reset After Code Was Already Pushed

If history was already pushed to GitHub, a normal push may be rejected after resetting.

For intentional history rewriting on a safe practice branch:

```bash
git push --force-with-lease origin branch-name
```

`--force-with-lease` is safer than:

```bash
git push --force
```

For important shared branches, `git revert` is usually safer:

```bash
git revert <commit-id>
git push
```

`git revert` creates a new commit that reverses an old commit.

It does not remove the old commit from history.

---

## Recover After an Accidental Reset

Check recent Git movements:

```bash
git reflog
```

Find the old commit.

Then:

```bash
git reset --mixed <old-commit-id>
```

A safety branch can also be created before practicing:

```bash
git branch backup-before-reset
```

---

## Reset Summary

```text
--soft
= remove commit
= changes stay staged

--mixed
= remove commit
= changes stay
= changes become unstaged

--hard
= remove commit
= discard tracked changes
```

---

# 7. Git Stash

`git stash` temporarily saves unfinished changes without creating a commit.

---

## Why Use Git Stash

Example:

```text
Working on feature A
↓
Work is unfinished
↓
Urgent task arrives
↓
Need to switch branch
↓
git stash
↓
Unfinished work is temporarily hidden
↓
Complete urgent work
↓
Return
↓
Restore unfinished work
```

Simple idea:

```text
git stash
= temporarily put unfinished work aside
```

---

## Stash Tracked Changes

```bash
git stash
```

---

## Stash Tracked and Untracked Files

```bash
git stash -u
```

`-u` means:

```text
include untracked files
```

---

## Check Saved Stashes

```bash
git stash list
```

Example:

```text
stash@{0}: WIP on stash-practice: 1e469cc Merge pull request #5
```

Meaning:

```text
stash@{0}
= latest stash

WIP on stash-practice
= stash was created on stash-practice

1e469cc
= commit the branch pointed to at that time
```

---

## Restore with Pop

```bash
git stash pop
```

Meaning:

```text
Restore changes
+
Remove stash
```

---

## Restore with Apply

```bash
git stash apply
```

Meaning:

```text
Restore changes
+
Keep stash
```

---

## Pop vs Apply

```text
pop
= restore + remove

apply
= restore + keep
```

Easy memory:

```text
pop   = bring it back and remove backup
apply = bring it back and keep backup
```

---

## Delete a Stash

```bash
git stash drop stash@{0}
```

Check:

```bash
git stash list
```

---

## Git Stash Workflow

```text
Make unfinished changes
↓
git status
↓
git stash
or
git stash -u
↓
Changes are temporarily hidden
↓
Switch branch
↓
Do other work
↓
Come back
↓
git stash pop
or
git stash apply
```

---

# 8. Git Bisect

`git bisect` helps find which commit first introduced a bug.

It searches by repeatedly checking commits around the middle.

---

## Example

Suppose:

```text
Commit 1 ✅ Good
Commit 2 ✅ Good
Commit 3 ❌ Bug starts
Commit 4 ❌ Bad
Commit 5 ❌ Bad
```

The exact bad commit is unknown.

`git bisect` helps find it.

---

## Check Commit History

```bash
git log --oneline
```

Example:

```text
997a7cd Add divide function
84607ff Add multiply function
864230b Add subtract function
dde8a5d Add sub
51bbfef Add initial add function
```

---

## Start Bisect

```bash
git bisect start
```

Meaning:

```text
Start searching for the bad commit.
```

---

## Mark Current Commit as Bad

If the current version is broken:

```bash
git bisect bad
```

Example:

```text
Expected:

5 - 2 = 3

Actual:

5 - 2 = 7
```

So the current commit is bad.

---

## Mark an Older Good Commit

Suppose:

```text
51bbfef
```

was working.

Run:

```bash
git bisect good 51bbfef
```

Now Git knows:

```text
51bbfef = Good ✅

Current commit = Bad ❌
```

---

## How Git Bisect Searches

Git chooses a commit around the middle.

Example:

```text
Commit 1 ✅
Commit 2 ✅
Commit 3 ❓
Commit 4 ❌
Commit 5 ❌
```

Test the current version:

```bash
node calculator.js
```

If it works:

```bash
git bisect good
```

If it is broken:

```bash
git bisect bad
```

Git removes half of the remaining search area.

It repeats until the first bad commit is found.

This method is called:

```text
Binary Search
```

---

## Example Search

```text
1 ✅   2 ✅   3 ❌   4 ❌   5 ❌
               ↑
         Git checks here
```

If Commit 3 is bad:

```text
The bug must be between Commit 1 and Commit 3.
```

Git can ignore Commit 4 and Commit 5.

Then it checks the remaining commits.

---

## First Bad Commit

In the practice example, Git found:

```text
864230b
```

Git showed:

```text
864230b is the first bad commit
```

Meaning:

```text
Before 864230b
= working ✅

864230b
= bug introduced ❌

After 864230b
= bug continues ❌
```

---

## End Git Bisect

```bash
git bisect reset
```

This ends bisect mode and returns to the original branch position.

---

## Git Bisect Workflow

```text
Bug found
↓
git log --oneline
↓
Find one known good commit
↓
git bisect start
↓
git bisect bad
↓
git bisect good <good-commit-id>
↓
Git checks a middle commit
↓
Test code
↓
Working → git bisect good
Broken  → git bisect bad
↓
Repeat
↓
Git finds first bad commit
↓
git bisect reset
```

---

# 9. Quick Command Reference

## Basic Git

```bash
git init
git status
git add .
git commit -m "message"
git push
git pull
```

---

## Branches

```bash
git branch
git branch -r
git branch branch-name
git switch branch-name
git fetch
```

---

## Remote

```bash
git remote -v
git remote add origin <repository-url>
```

---

## Reset

```bash
git reset --soft HEAD~1
git reset --mixed HEAD~1
git reset --hard HEAD~1
git reflog
```

---

## Stash

```bash
git stash
git stash -u
git stash list
git stash pop
git stash apply
git stash drop stash@{0}
```

---

## Bisect

```bash
git bisect start
git bisect bad
git bisect good <commit-id>
git bisect good
git bisect bad
git bisect reset
```

---

# Overall Git Workflow

```text
Create / change code
↓
git status
↓
git add
↓
git commit
↓
git push
↓
Create Pull Request
↓
Code Review
↓
Merge
↓
git switch main
↓
git pull
```

---

# Main Concepts to Remember

```text
Git
= tracks code changes locally

GitHub
= stores and shares Git repositories online

Branch
= separate line of development

Commit
= saved snapshot

Staging
= changes selected for the next commit

Pull Request
= request to merge branch changes

Fetch
= check remote changes without applying them

Pull
= get and apply remote changes

Reset
= move branch back to another commit

Stash
= temporarily save unfinished work

Bisect
= find the commit that introduced a bug
```
```md
# 10. Git Diff

`git diff` is used to see what changed in the code.

Simple idea:

```text
git diff = show code differences
```

---

## Unstaged Changes

```bash
git diff
```

This shows changes that have been made but are not staged yet.

Example:

```diff
-console.log("Hello");
+console.log("Hello Git");
```

Meaning:

```text
- = old/removed line
+ = new/added line
```

---

## Staged Changes

After:

```bash
git add diff.js
```

normal `git diff` may show nothing.

To see staged changes:

```bash
git diff --staged
```

Simple difference:

```text
git diff
= unstaged changes

git diff --staged
= staged changes
```

---

## Compare Two Commits

First check commit history:

```bash
git log --oneline
```

Then compare:

```bash
git diff <old-commit-id> <new-commit-id>
```

Example:

```bash
git diff 2334291 c84fb5e
```

This shows what changed between the two commits.

---

# 11. Git Log

`git log` is used to see commit history.

---

## Detailed Commit History

```bash
git log
```

It shows:

```text
Commit ID
Author
Date
Commit message
```

---

## Short Commit History

```bash
git log --oneline
```

Example:

```text
c84fb5e Update greeting
2334291 Add diff practice file
```

Meaning:

```text
c84fb5e
= short commit ID

Update greeting
= commit message
```

---

## Show Latest Commits

Example:

```bash
git log -5
```

This shows the latest 5 commits.

---

## Show History of One File

```bash
git log --oneline -- filename
```

Example:

```bash
git log --oneline -- calculator.js
```

This shows commits related to `calculator.js`.

---

## Show Branch and Merge History

```bash
git log --oneline --graph --all
```

Meaning:

```text
--oneline
= show each commit in one line

--graph
= draw branch and merge lines

--all
= show commits from all branches and refs
```

---

## Important Git Log Symbols

```text
* = commit

| = history continues

\ = branch/history moves in another direction

/ = histories join together
```

Example:

```text
*   Merge pull request
|\
| * feature commit
| * feature commit
|/
*   older commit
```

Simple meaning:

```text
A branch had commits
↓
Then it was merged
```

---

## HEAD

Example:

```text
(HEAD -> diff-practice)
```

Means:

```text
You are currently on the diff-practice branch.
```

---

## Local and Remote Main

Example:

```text
(main, origin/main)
```

Meaning:

```text
main
= local main branch

origin/main
= GitHub main branch
```

If both are beside the same commit, they are pointing to the same commit.

---

## Exit Git Log Viewer

If Git opens a long log screen, press:

```text
q
```

to quit.

---

# 12. Git Ignore

`.gitignore` tells Git which files or folders should not be tracked.

Simple idea:

```text
.gitignore
= files Git should ignore
```

---

## Create `.gitignore`

Create a file named exactly:

```text
.gitignore
```

Not:

```text
gitignore
.gitignore.txt
gitignore.txt
```

---

## Ignore a File

Example:

```gitignore
.env
```

This tells Git to ignore the `.env` file.

---

## Ignore a Folder

Example:

```gitignore
node_modules/
```

This tells Git to ignore the entire `node_modules` folder.

---

## Ignore a File Type

Example:

```gitignore
*.log
```

This ignores all files ending with:

```text
.log
```

---

## Add Comments

Use `#` for comments:

```gitignore
# Environment files
.env

# Dependencies
node_modules/

# Logs
*.log
```

---

## Basic Node.js `.gitignore`

```gitignore
# Dependencies
node_modules/

# Environment files
.env

# Logs
*.log

# Build folders
dist/
build/
```

---

## Important `.gitignore` Rule

`.gitignore` works best for files that are not already tracked.

If a file was already committed before adding it to `.gitignore`, Git may continue tracking it.

---

# 13. Merge Conflicts

A merge conflict happens when Git cannot decide which code to keep.

This usually happens when two branches change the same part of the same file differently.

---

## Example

Branch A:

```js
console.log("Hello from branch A");
```

Branch B:

```js
console.log("Hello from branch B");
```

When Git tries to merge them, it cannot automatically choose one.

So Git creates a merge conflict.

---

## Conflict Markers

Git may show:

```text
<<<<<<< HEAD
console.log("Hello from branch B");
=======
console.log("Hello from branch A");
>>>>>>> conflict-a
```

Meaning:

```text
<<<<<<< HEAD
= current branch code

=======
= separator

>>>>>>> conflict-a
= incoming branch code
```

If the current branch is `conflict-b`:

```text
Current Change
= conflict-b

Incoming Change
= conflict-a
```

---

## Resolve Conflict in VS Code

VS Code may show:

```text
Accept Current Change
Accept Incoming Change
Accept Both Changes
```

Meaning:

```text
Accept Current Change
= keep current branch code

Accept Incoming Change
= keep incoming branch code

Accept Both Changes
= keep both versions
```

---

## Resolve Conflict Manually

Choose the final code.

For example:

```js
console.log("Hello from branch B");
```

Then remove:

```text
<<<<<<< HEAD
=======
>>>>>>> conflict-a
```

---

## Mark Conflict as Resolved

After fixing the file:

```bash
git add conflicts.js
```

Then commit:

```bash
git commit -m "Resolve merge conflict"
```

---

## Merge Conflict Workflow

```text
Merge branches
↓
Conflict happens
↓
Choose final code
↓
Remove conflict markers
↓
git add <file>
↓
git commit
↓
Conflict resolved
```

---

## Cancel a Merge

If the merge becomes confusing or the wrong branch was merged:

```bash
git merge --abort
```

Simple meaning:

```text
Cancel the merge
and
go back to the state before the merge started
```

---

## Important Merge Conflict Rule

Before committing, make sure:

```text
<<<<<<<
=======
>>>>>>>
```

are removed from the file.

Then:

```bash
git add <file>
git commit -m "Resolve merge conflict"
```

---

# Quick Summary

## Git Diff

```bash
git diff
```

Show unstaged changes.

```bash
git diff --staged
```

Show staged changes.

```bash
git diff <commit1> <commit2>
```

Compare two commits.

---

## Git Log

```bash
git log
```

Detailed history.

```bash
git log --oneline
```

Short history.

```bash
git log --oneline --graph --all
```

Show branch and merge history.

---

## Git Ignore

```gitignore
.env
node_modules/
*.log
```

Ignore files, folders, and file types.

---

## Merge Conflict

```text
Two branches change the same code
↓
Git cannot choose
↓
Conflict
↓
Choose final code
↓
git add
↓
git commit
```

Cancel the merge:

```bash
git merge --abort
```
```
