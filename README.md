# Git Complete Beginner's Guide - Top 15 Commands

A hands-on lab guide to learn Git from scratch. Follow each section in order.

---

## Prerequisites

1. **Install Git** → [https://git-scm.com/downloads](https://git-scm.com/downloads)
2. **Create a GitHub account** → [https://github.com](https://github.com)
3. Verify installation:

```bash
git --version
```

---

## Initial Setup (One-time Configuration)

Before using Git, configure your identity:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

Verify your config:

```bash
git config --list
```

---

## Top 15 Git Commands with Examples

---

### 1. `git init` — Initialize a New Repository

Creates a new Git repository in your current folder.

```bash
mkdir my-first-project
cd my-first-project
git init
```

**Output:**
```
Initialized empty Git repository in /my-first-project/.git/
```

> This creates a hidden `.git` folder that tracks all changes.

---

### 2. `git status` — Check Repository Status

Shows which files are tracked, modified, or staged.

```bash
git status
```

**Try it:**
```bash
echo "Hello World" > hello.txt
git status
```

**Output:**
```
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        hello.txt
```

---

### 3. `git add` — Stage Files for Commit

Moves files to the staging area (ready to be committed).

```bash
# Add a single file
git add hello.txt

# Add all files in the current directory
git add .

# Add all files with a specific extension
git add *.txt
```

**Try it:**
```bash
git add hello.txt
git status
```

**Output:**
```
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   hello.txt
```

---

### 4. `git commit` — Save Changes to Repository

Records the staged changes with a message describing what you did.

```bash
git commit -m "Add hello.txt file"
```

**Output:**
```
[main (root-commit) abc1234] Add hello.txt file
 1 file changed, 1 insertion(+)
 create mode 100644 hello.txt
```

**Common variations:**
```bash
# Stage and commit all modified files in one step
git commit -am "Update existing files"

# Commit with a detailed message
git commit -m "feat: add user login functionality"
```

---

### 5. `git log` — View Commit History

Shows a list of all commits made in the repository.

```bash
# Full log
git log

# One-line summary per commit
git log --oneline

# Show last 5 commits
git log --oneline -5

# Graphical view of branches
git log --oneline --graph --all
```

**Output (oneline):**
```
abc1234 Add hello.txt file
```

---

### 6. `git diff` — View Changes

Shows the differences between your working files and the last commit.

```bash
# See unstaged changes
git diff

# See staged changes (ready to commit)
git diff --staged

# Compare two commits
git diff abc1234 def5678
```

**Try it:**
```bash
echo "Hello Git" >> hello.txt
git diff
```

**Output:**
```
+Hello Git
```

---

### 7. `git branch` — Manage Branches

Branches let you work on features without affecting the main code.

```bash
# List all branches
git branch

# Create a new branch
git branch feature-login

# Rename a branch
git branch -m old-name new-name

# Delete a branch
git branch -d feature-login
```

---

### 8. `git checkout` / `git switch` — Switch Branches

Move between branches or create and switch in one step.

```bash
# Switch to an existing branch
git checkout feature-login
# OR (modern way)
git switch feature-login

# Create and switch to a new branch in one step
git checkout -b feature-signup
# OR (modern way)
git switch -c feature-signup
```

---

### 9. `git merge` — Merge Branches

Combines changes from one branch into another.

```bash
# First, switch to the branch you want to merge INTO
git checkout main

# Then merge the feature branch
git merge feature-login
```

**Example workflow:**
```bash
git checkout -b feature-about
echo "About page content" > about.txt
git add about.txt
git commit -m "Add about page"
git checkout main
git merge feature-about
```

---

### 10. `git remote` — Manage Remote Repositories

Links your local repo to GitHub (or any remote server).

```bash
# Add a remote repository (do this once after git init)
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git

# View configured remotes
git remote -v

# Remove a remote
git remote remove origin
```

---

### 11. `git push` — Upload to GitHub

Sends your committed changes to the remote repository.

```bash
# Push to main branch (first time, set upstream)
git push -u origin main

# After first push, just use:
git push

# Push a specific branch
git push origin feature-login
```

---

### 12. `git pull` — Download from GitHub

Fetches and merges changes from the remote repository.

```bash
# Pull latest changes
git pull

# Pull from a specific branch
git pull origin main
```

---

### 13. `git clone` — Copy a Remote Repository

Downloads an entire repository from GitHub to your local machine.

```bash
# Clone using HTTPS
git clone https://github.com/USERNAME/REPOSITORY.git

# Clone into a specific folder
git clone https://github.com/USERNAME/REPOSITORY.git my-folder

# Clone a specific branch
git clone -b branch-name https://github.com/USERNAME/REPOSITORY.git
```

---

### 14. `git stash` — Temporarily Save Changes

Saves your uncommitted changes without committing, so you can switch branches.

```bash
# Stash current changes
git stash

# List all stashes
git stash list

# Restore the most recent stash
git stash pop

# Restore a specific stash
git stash apply stash@{0}

# Delete all stashes
git stash clear
```

**Example:**
```bash
echo "work in progress" > wip.txt
git add wip.txt
git stash
# Now your working directory is clean
git stash pop
# Changes are restored
```

---

### 15. `git reset` — Undo Changes

Removes files from staging or reverts commits.

```bash
# Unstage a file (keep changes in working directory)
git reset hello.txt

# Unstage all files
git reset

# Undo the last commit (keep changes in working directory)
git reset --soft HEAD~1

# Undo the last commit (discard changes — DANGEROUS)
git reset --hard HEAD~1
```

---

## Complete Lab: Push Your Code to GitHub

Follow these steps to create a project and push it to GitHub.

### Step 1: Create a GitHub Repository

1. Go to [https://github.com/new](https://github.com/new)
2. Enter repository name: `sahasra-project`
3. Keep it **Public** or **Private**
4. **DO NOT** check "Add a README" (we already have one)
5. Click **Create repository**

### Step 2: Initialize and Push

```bash
# Navigate to your project folder
cd c:\Users\Dell\sahasra-project

# Initialize git
git init

# Add all files
git add .

# Make your first commit
git commit -m "Initial commit: add project files"

# Connect to GitHub (replace YOUR-USERNAME)
git remote add origin https://github.com/YOUR-USERNAME/sahasra-project.git

# Rename default branch to main (if needed)
git branch -M main

# Push to GitHub
git push -u origin main
```

### Step 3: Verify

1. Go to `https://github.com/YOUR-USERNAME/sahasra-project`
2. You should see your files on GitHub!

---

## Complete Lab: Clone a Repository

```bash
# Clone any public repository
git clone https://github.com/YOUR-USERNAME/sahasra-project.git

# Enter the cloned folder
cd sahasra-project

# View the files
ls

# Check the remote connection
git remote -v
```

---

## Complete Lab: Make Changes and Push Again

```bash
# Make a change
echo "New feature added" >> hello.txt

# Check what changed
git status
git diff

# Stage, commit, and push
git add .
git commit -m "Update hello.txt with new feature"
git push
```

---

## Complete Lab: Work with Branches

```bash
# Create and switch to a new branch
git checkout -b feature-new-page

# Create a new file
echo "New page content" > newpage.txt

# Stage and commit
git add newpage.txt
git commit -m "Add new page"

# Push the branch to GitHub
git push -u origin feature-new-page

# Switch back to main
git checkout main

# Merge the feature branch
git merge feature-new-page

# Push the merged main branch
git push
```

---

## Git Workflow Cheat Sheet

```
Working Directory → Staging Area → Local Repository → Remote Repository
     git add          git commit         git push
     
Remote Repository → Local Repository
     git clone (first time)
     git pull  (subsequent updates)
```

### Daily Workflow

```bash
git pull                    # Get latest changes
# ... make your changes ...
git add .                   # Stage changes
git commit -m "message"     # Commit changes
git push                    # Push to GitHub
```

---

## Common Issues & Fixes

| Problem | Solution |
|---------|----------|
| `fatal: not a git repository` | Run `git init` first |
| `error: failed to push` | Run `git pull` first, then `git push` |
| `merge conflict` | Open the conflicted file, edit it, then `git add` and `git commit` |
| `detached HEAD` | Run `git checkout main` to go back |
| Wrong commit message | `git commit --amend -m "new message"` (before push only) |

---

## GitHub Authentication

If GitHub asks for credentials when pushing:

### Option A: HTTPS with Personal Access Token
1. Go to GitHub → Settings → Developer Settings → Personal Access Tokens → Tokens (classic)
2. Generate a new token with `repo` scope
3. Use the token as your password when pushing

### Option B: SSH Key (Recommended)
```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"

# Copy the public key
cat ~/.ssh/id_ed25519.pub

# Add the key to GitHub:
# GitHub → Settings → SSH and GPG Keys → New SSH Key → Paste the key

# Use SSH remote URL
git remote set-url origin git@github.com:YOUR-USERNAME/sahasra-project.git
```

---

## Quick Reference Table

| # | Command | Purpose |
|---|---------|---------|
| 1 | `git init` | Initialize a new repository |
| 2 | `git status` | Check file status |
| 3 | `git add` | Stage files |
| 4 | `git commit` | Save changes |
| 5 | `git log` | View history |
| 6 | `git diff` | View changes |
| 7 | `git branch` | Manage branches |
| 8 | `git checkout/switch` | Switch branches |
| 9 | `git merge` | Merge branches |
| 10 | `git remote` | Manage remotes |
| 11 | `git push` | Upload to GitHub |
| 12 | `git pull` | Download from GitHub |
| 13 | `git clone` | Copy a repository |
| 14 | `git stash` | Temporarily save work |
| 15 | `git reset` | Undo changes |

---

Happy Learning! Start from Command #1 and work your way down. Practice each command before moving to the next.
