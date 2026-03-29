# 03 - Basic Git Commands

## 📦 **Setting Up a Repository**

### **Create New Repository Locally**

```bash
mkdir my-project
cd my-project
git init
```

**What it does:** Creates a `.git` folder (Git tracks all changes here)

### **Clone Existing Repository**

```bash
git clone https://github.com/username/repository.git
cd repository
```

**What it does:** Downloads entire repo with all history

**Example:**
```bash
git clone https://github.com/torvalds/linux.git
```

---

## 📝 **Checking Status**

### **See Current Status**

```bash
git status
```

**Output shows:**
- Current branch
- Modified files (red)
- Staged files (green)
- Untracked files

**Example output:**
```
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  modified:   README.md

Untracked files:
  .DS_Store
  new-file.txt
```

### **View Commit History**

```bash
git log
```

**Shows:**
- Commit hash (unique ID)
- Author name and email
- Date
- Commit message

**Options:**
```bash
git log --oneline              # Compact format
git log --graph --all --oneline   # Visual branch graph
git log -5                     # Last 5 commits
git log --author="Name"        # Commits by specific author
git log --grep="keyword"       # Search commit messages
```

### **View File Changes**

```bash
git diff                       # Show changes not staged
git diff --staged              # Show changes to be committed
git diff HEAD                  # All changes since last commit
```

---

## 🎯 **Core Workflow: Add → Commit → Push**

### **Step 1: Modify Files**

```bash
# Your text editor or IDE
# Edit or create files
# Save files
```

### **Step 2: Stage Changes (Add)**

```bash
git add filename.txt           # Stage specific file
git add src/                   # Stage entire folder
git add .                      # Stage all changes
```

**What it does:** Prepares files for commit (staging area)

```
Untracked/Modified Files
         ↓
    git add
         ↓
    Staging Area
         ↓
    git commit
         ↓
    Local Repository
```

### **Step 3: Commit Changes**

```bash
git commit -m "Your message"
```

**Commit message guidelines:**
- Be clear and descriptive
- Start with verb: Fix, Add, Update, Remove, Refactor
- Keep it concise (50 characters max for subject)

**Good messages:**
```bash
git commit -m "Fix login validation error"
git commit -m "Add user authentication feature"
git commit -m "Update README with new instructions"
```

**Bad messages:**
```bash
git commit -m "stuff"
git commit -m "fixed things"
git commit -m "."
```

### **Step 4: Push to Remote**

```bash
git push                       # Push to current branch
git push origin branch-name    # Push specific branch
git push -u origin branch-name # Push and set upstream
```

**What it does:** Uploads commits to GitHub

---

## 🌳 **Working with Branches**

### **List Branches**

```bash
git branch                     # Local branches
git branch -a                  # All branches (local + remote)
git branch -r                  # Remote branches only
```

### **Create New Branch**

```bash
git branch feature-name        # Create branch
git checkout feature-name      # Switch to branch
# OR combined:
git checkout -b feature-name   # Create and switch
# OR newer syntax:
git switch -c feature-name     # Create and switch
```

### **Switch Branches**

```bash
git checkout branch-name       # Switch to branch
git switch branch-name         # Newer way
```

**Before switching:** commit or stash your changes!

### **Delete Branch**

```bash
git branch -d branch-name      # Delete locally
git branch -D branch-name      # Force delete
git push origin --delete branch-name  # Delete remote
```

---

## 🔄 **Updating Your Local Repository**

### **Pull Latest Changes**

```bash
git pull                       # Combine fetch + merge
git pull origin main           # Pull specific branch
```

**What it does:**
1. Downloads latest changes from GitHub
2. Merges them into your branch

### **Fetch Only (Don't Merge)**

```bash
git fetch                      # Download only
git fetch origin               # From specific remote
```

**What it does:** Download changes but don't merge yet

---

## ↩️ **Undoing Changes**

### **Before You Commit (Undo in Working Directory)**

```bash
git checkout -- filename       # Discard changes in file
git restore filename           # Newer way
```

**⚠️ Warning:** This permanently deletes your changes!

### **After Staging (Remove from Staging Area)**

```bash
git reset HEAD filename        # Unstage file
git restore --staged filename  # Newer way
```

**File still has changes, just not staged**

### **After Committing (Undo Commit)**

```bash
git revert commit-hash         # Create new commit undoing changes
git reset --soft HEAD~1        # Undo last commit, keep changes
git reset --hard HEAD~1        # Undo last commit, discard changes
```

**⚠️ Be careful with reset!**

---

## 📍 **Remote Repository Commands**

### **Add Remote**

```bash
git remote add origin https://github.com/username/repo.git
```

### **View Remotes**

```bash
git remote                     # List remote names
git remote -v                  # List with URLs
```

### **Change Remote URL**

```bash
git remote set-url origin https://new-url.git
```

### **Remove Remote**

```bash
git remote remove origin
```

---

## 🏷️ **Tags (Marking Versions)**

### **Create Tag**

```bash
git tag v1.0.0                 # Lightweight tag
git tag -a v1.0.0 -m "Version 1.0"  # Annotated
```

### **Push Tags**

```bash
git push origin v1.0.0         # Push specific tag
git push origin --tags         # Push all tags
```

### **View Tags**

```bash
git tag                        # List all tags
```

---

## 📊 **Useful Command Combinations**

### **Daily Workflow**

```bash
# Start day
git pull              # Get latest

# Make changes
# ... edit files ...

# Before lunch
git add .
git commit -m "WIP: working on feature"
git push

# End of day
git add .
git commit -m "Feature complete: user authentication"
git push
```

### **Create and Push New Feature**

```bash
git checkout -b feature/new-feature
# ... make changes ...
git add .
git commit -m "Add new feature"
git push -u origin feature/new-feature
```

### **Sync with Main**

```bash
git fetch origin
git merge origin/main
```

---

## 🧹 **Cleaning Up**

### **Remove Untracked Files**

```bash
git clean -fd                  # Remove untracked files and folders
git clean -fdn                 # Dry run (preview)
```

### **Remove Ignored Files**

```bash
git clean -fdx                 # Remove ignored files too
```

---

## 📚 **Command Reference Table**

| Command | Purpose |
|---------|---------|
| `git init` | Initialize new repo |
| `git clone` | Copy repo to computer |
| `git status` | Check current status |
| `git add` | Stage files |
| `git commit` | Save changes |
| `git push` | Upload to GitHub |
| `git pull` | Download & merge |
| `git branch` | Manage branches |
| `git checkout` | Switch branches |
| `git log` | View history |
| `git diff` | Show changes |
| `git revert` | Undo commit safely |
| `git reset` | Undo changes (be careful!) |
| `git merge` | Combine branches |
| `git tag` | Mark versions |

---

## 💡 **Pro Tips**

✅ **Commit often** - Small commits are easier to review  
✅ **Write clear messages** - Future you will thank you  
✅ **Pull before you push** - Avoid conflicts  
✅ **Use branches** - Keep main stable  
✅ **Review before committing** - `git diff` before `git add`  

---

## ✨ **Next Steps**

Now you know the basic commands! Learn about: **04-Branches-Workflow.md**

You'll learn professional branching strategies and workflows.
