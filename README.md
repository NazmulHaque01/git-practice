# 🌱 GitHub Basics — Personal Notebook

> A concise personal reference for Git & GitHub concepts, commands, and workflows.

---
> SEE NOTEBOOK IN WEBSITE : https://nazmulhaque01.github.io/git-practice/

---


## 📖 Table of Contents

- [What is GitHub?](#-what-is-github)
- [Core Concepts](#-core-concepts)
- [How GitHub Works](#-how-github-works-simple-story)
- [Git Setup & First-Time Config](#-git-setup--first-time-config)
- [Daily Workflow Loop](#-daily-workflow-loop)
- [Branching & Merging](#-branching--merging)
- [Going Back to Previous Versions](#-going-back-to-previous-versions)

---

## 🌐 What is GitHub?

GitHub is a website where people **store code**, **work together**, and **keep track of changes**.
Think of it like Google Drive — but *specially designed for coding*, with superpowers.

GitHub uses a tool called **Git**, which acts like a **time machine for your code**.

---

## 🧩 Core Concepts

| Concept | What It Means |
|---|---|
| **Repository (Repo)** | A folder on GitHub that contains your project files and remembers every change ever made |
| **Commit** | Saving your work with a message — like a checkpoint in a game |
| **Branch** | A safe copy of your project where you can experiment without breaking the main version |
| **Merge** | Combining a branch back into the main project after experiments succeed |
| **Pull Request (PR)** | A *proposal* to merge your changes — team reviews, comments, and approves |
| **Clone** | Downloading a full copy of a GitHub repo to your computer |
| **Push** | Uploading your local changes to GitHub |
| **Pull** | Downloading the latest changes from GitHub to your computer |
| **Fork** | Your own copy of *someone else's* repo |
| **Issues** | To-do tasks or bug reports (e.g. "Login button broken", "Add dark mode") |
| **README.md** | The homepage of your repo — explains what, how to install, and how to use |
| **Git** | The engine behind GitHub — tracks all changes locally |

### 🔁 Push vs Pull vs Clone vs Fork

```
Clone  → Download a repo to your computer (once, to start)
Push   → Upload your local changes → GitHub
Pull   → Download latest changes ← GitHub
Fork   → Copy someone else's entire repo into your own GitHub account
```

> **Note on Pull Request:** Despite the name, it's about **merging**, not downloading.

---

## 🧠 How GitHub Works (Simple Story)

Imagine you're **writing a book**:

```
📁 Create a repo         →  Your book folder
✍️  Write a chapter       →  Make a commit
🌿 Try a new ending      →  Create a branch
✅ Like the new ending   →  Merge it
💬 Want feedback         →  Open a pull request
🐛 Someone finds a typo  →  They open an issue
```

> That's GitHub in a nutshell.

---

## ⚙️ Git Setup & First-Time Config

### 1. Download & Install Git
[https://git-scm.com](https://git-scm.com)

### 2. Open Git Bash
In your project folder → Right-click → **Open Git Bash Here**

### 3. Introduce Yourself to Git

```bash
git config --global user.name "YourGitHubUsername"
git config --global user.email "your-github-email@example.com"
```

| Flag | Scope |
|---|---|
| `--local` | Only for the current folder/project |
| `--global` | All folders on your account *(recommended)* |
| `--system` | All users on the PC |

### 4. Initialize Git in Your Project *(run once per project)*

```bash
git init
```

### 5. Add Files to Staging

```bash
git add index.html          # specific file
git add .                   # all files
git add folder-name         # all files in a folder
git add *.html              # all .html files
```

### 6. Commit Your Changes

```bash
git commit -m "Your message describing the changes"
```

### 7. Connect to a GitHub Repository *(run once per project)*

First, create the repo on GitHub. Then:

```bash
git remote add origin https://github.com/YourUsername/your-repo.git
```

> `origin` = short alias for the full repository URL

### 8. Create & Name the Main Branch

```bash
git branch -M main
```

> `-M` = move/rename the branch. `main` is the standard name.

### 9. Push for the First Time

```bash
git push -u origin main
```

> `-u` saves the `origin` and branch so next time you only need `git push`

---

## 🔄 Daily Workflow Loop

```
Make changes  →  git status  →  git add .  →  git commit -m "msg"  →  git push
```

```bash
git status                        # See what changed
git add .                         # Stage everything
git commit -m "describe change"   # Save a checkpoint
git push                          # Upload to GitHub
```

### Check All Commits

```bash
git log           # Full log
git log --oneline # Short, compact log (shows 7-digit hash IDs)
```

---

## 🌿 Branching & Merging

### Create a Branch & Switch to It

```bash
git checkout -b branch-name
```

Then do your work and repeat the loop → `add` → `commit` → `push`

```bash
git push -u origin branch-name
```

### Branch Management Commands

```bash
git branch -a                        # List all branches (local + remote)
git branch -d branch-name           # Delete branch locally
git push origin --delete branch-name # Delete branch from GitHub too
```

### Merge a Branch into Main

```bash
git checkout main           # Switch to main first
git merge branch-name       # Merge your branch into main
```

### Change the Default Branch

Go to **GitHub website → Repo Settings → Default Branch → Change it**

Then update your local Git to reflect it:

```bash
git remote set-head origin -a    # -a = auto-detect
```

---

## ⏪ Going Back to Previous Versions

> Always run `git log --oneline` first to find the **7-digit hash ID** of the target commit.

---

### ✅ Method 1 — RECOMMENDED

**View old code without permanently changing anything:**

```bash
git checkout hash-id        # See old version locally
```

**Make old version permanent (as a new commit):**

```bash
git checkout hash-id .      # Copy old code to local
git commit -m "Reverted to vX"
git push
```

> This keeps V1, V2, V3 history intact — just adds a new commit that matches V1.

---

### ⚠️ Method 2 — Hard Reset (Destructive)

**Removes all commits after the target — use with caution:**

```bash
git reset --hard hash-id-of-v1
git push -f
```

> ❗ This **deletes** all newer commits permanently.

---

### ❌ Method 3 — NOT RECOMMENDED

Using `git revert` to go back step by step:

```bash
git revert hash-of-v3       # Goes back to V2
git revert hash-of-v2       # Goes back to V1
git push
```

> Very confusing and requires extra steps. Avoid unless you understand it well.

---

## 📌 Quick Reference Card

```bash
git init                              # Initialize repo
git status                            # Check changes
git add .                             # Stage all files
git commit -m "message"              # Save checkpoint
git push                              # Upload to GitHub
git pull                              # Download from GitHub
git log --oneline                     # View all commits (short)
git checkout -b new-branch           # Create & switch to branch
git checkout main                    # Switch to main
git merge branch-name                # Merge branch into current
git clone <url>                       # Download a repo
git remote add origin <url>          # Connect to GitHub repo
git branch -a                        # List all branches
git reset --hard <hash>              # Hard reset to old commit
git checkout <hash> .                # Copy old version to local
```

---

*Personal notebook by [NazmulHaque01](https://github.com/NazmulHaque01)*
