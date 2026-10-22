# Experiment: Branching, Merging, Rebasing and Resolving Merge Conflicts in Git

## 1. Aim

To implement branching, merging, rebasing, and resolve merge conflicts using Git.

## 2. Introduction

Git is a distributed version control system that allows developers to track changes in files and collaborate on projects.

* **Branching:** Creates a separate line of development.
* **Merging:** Combines changes from one branch into another.
* **Rebasing:** Reapplies commits on top of another branch.
* **Merge Conflict:** Occurs when Git cannot automatically combine changes, such as when two branches modify the same lines of a file.

## 3. Requirements

* Operating System: Windows
* Git installed and configured
* Git Bash or terminal
* GitHub account (optional)

## 4. Create a Local Repository

Create a project folder and initialize Git:

```bash
mkdir git-branching-lab
cd git-branching-lab
git init -b main
```

Configure Git if it has not already been configured:

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

Create a sample file:

```bash
echo "Project started" > notes.txt
git add notes.txt
git commit -m "Initial commit"
```

## 5. Branching

Create a new branch and switch to it:

```bash
git branch feature
git switch feature
```

Add a change and commit it:

```bash
echo "Feature developed" >> notes.txt
git add notes.txt
git commit -m "Add feature"
```

Switch back to the main branch:

```bash
git switch main
```

List the branches:

```bash
git branch
```

## 6. Merging

Merge the feature branch into the main branch:

```bash
git merge feature
```

This combines the changes from the feature branch into the current branch, provided Git can merge them automatically.

## 7. Rebasing

Create another branch:

```bash
git switch -c update-feature
echo "Feature update" >> notes.txt
git add notes.txt
git commit -m "Update feature"
```

Rebase it onto the main branch:

```bash
git rebase main
```

Rebasing reapplies the branch's commits on top of the latest commit of the target branch.

## 8. Resolving Merge Conflicts

A merge conflict occurs when two branches make incompatible changes to the same part of a file.

### Step 1: Create a conflict

Switch to the main branch:

```bash
git switch main
```

Add a line to the file and commit it:

```bash
echo "Updated by main" >> notes.txt
git add notes.txt
git commit -m "Update notes in main"
```

Switch to the feature branch:

```bash
git switch feature
```

Add a different line and commit it:

```bash
echo "Updated by feature" >> notes.txt
git add notes.txt
git commit -m "Update notes in feature"
```

### Step 2: Merge the branches

Switch to main:

```bash
git switch main
git merge feature
```

Git may report a conflict if both branches changed the same lines.

### Step 3: Resolve the conflict

Open `notes.txt` in a text editor.

A conflicting file may contain:

```text
<<<<<<< HEAD
Updated by main
=======
Updated by feature
>>>>>>> feature
```

Edit the file to retain the content you want. For example:

```text
Updated by main
Updated by feature
```

Remove the conflict markers.

### Step 4: Complete the merge

Stage the resolved file and commit the merge:

```bash
git add notes.txt
git commit -m "Resolve merge conflict"
```

Verify the repository status:

```bash
git status
```

## 9. View Commit History

Display the commit history and branch structure:

```bash
git log --oneline --graph --all
```

This command displays commits from all branches in a graphical format.

## 10. Conclusion

Branching, merging, and rebasing were demonstrated using Git. A merge conflict was created, resolved manually, and committed successfully. These operations help developers manage parallel development and maintain project history.
