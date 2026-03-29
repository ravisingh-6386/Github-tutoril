# 08 - Git & GitHub Cheat Sheet

## ⚡ **Quick Command Reference**

### **Setup & Configuration**

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git config --global --list              # View all settings
git config --global core.editor "code"  # Set default editor
```

---

### **Basic Workflow**

```bash
git init                    # Create new repo
git clone <url>             # Download repo
git status                  # Check current status
git add <file>              # Stage specific file
git add .                   # Stage all changes
git commit -m "message"     # Save changes
git push                    # Upload to GitHub
git pull                    # Download and merge
```

---

### **Viewing History**

```bash
git log                     # View commit history
git log --oneline           # One line per commit
git log --graph --all       # Visual branch tree
git log -n 5                # Last 5 commits
git log --author="Name"     # By specific author
git log --since="2 weeks ago"
git show <commit-hash>      # Show commit details
git diff                    # Show unstaged changes
git diff --staged           # Show staged changes
git diff <branch1> <branch2>  # Compare branches
```

---

### **Branches**

```bash
git branch                  # List local branches
git branch -a               # All branches
git branch <branch-name>    # Create branch
git checkout <branch-name>  # Switch branch
git checkout -b <branch>    # Create and switch
git switch -c <branch>      # Create and switch (newer)
git branch -d <branch>      # Delete branch
git branch -D <branch>      # Force delete
git branch -m old new       # Rename branch
git push origin --delete <branch>  # Delete remote
```

---

### **Merging**

```bash
git merge <branch-name>     # Merge branch into current
git merge --no-ff <branch>  # Merge with commit
git merge --squash <branch> # Combine commits
git rebase <branch-name>    # Reapply commits
git merge --abort           # Cancel merge (if conflicts)
```

---

### **Undoing Changes**

```bash
git restore <file>          # Discard changes (local)
git restore --staged <file> # Unstage file
git reset HEAD <file>       # Unstage (older way)
git reset --soft HEAD~1     # Undo last commit (keep changes)
git reset --hard HEAD~1     # Undo last commit (discard)
git revert <commit>         # Create new commit undoing changes
git clean -fd               # Remove untracked files
```

---

### **Stashing**

```bash
git stash                   # Save changes temporarily
git stash list              # View saved stashes
git stash pop               # Restore and remove
git stash apply             # Restore but keep stash
git stash drop              # Delete stash
```

---

### **Remote Management**

```bash
git remote                  # List remotes
git remote -v               # List with URLs
git remote add origin <url> # Add remote
git remote set-url origin <url>  # Change URL
git remote remove origin    # Remove remote
git fetch                   # Download (no merge)
git push                    # Upload commits
git push origin <branch>    # Push specific branch
git push -u origin main     # Set upstream
git push origin --delete <branch>  # Delete remote
git pull                    # Fetch + merge
```

---

### **Tags (Versions)**

```bash
git tag                     # List tags
git tag <tag-name>          # Create lightweight tag
git tag -a <tag> -m "msg"   # Create annotated tag
git push origin <tag>       # Push specific tag
git push origin --tags      # Push all tags
git tag -d <tag>            # Delete local tag
git push origin --delete <tag>  # Delete remote
```

---

### **Searching**

```bash
git log --grep="text"       # Search commit messages
git log -S "code"           # Search in code changes
git log --oneline | grep "keyword"   # Combine with grep
git blame <file>            # See who changed each line
git bisect                  # Binary search for bug
```

---

## 🐙 **GitHub Web Interface**

### **Pull Requests**
1. Go to repository → Pull Requests
2. Click "New Pull Request"
3. Select branches: base ← compare
4. Add title and description
5. Request reviewers
6. Submit PR

### **Issues**
1. Go to Issues tab
2. Click "New issue"
3. Add title and description
4. Add labels (bug, feature, etc.)
5. Assign to person
6. Submit

### **Creating Release**
1. Go to Releases (right sidebar)
2. Click "Create new release"
3. Enter tag (v1.0.0)
4. Add title and notes
5. Attach files (optional)
6. Publish

---

## 📊 **Common Workflows**

### **Daily Workflow**

```bash
# Start day
git checkout main
git pull origin main

# Work on feature
git checkout -b feature/task
# ... make changes ...

# Commit frequently
git add .
git commit -m "work on feature"

# Keep in sync
git fetch origin
git merge origin/main

# Push when ready
git push origin feature/task

# After approval (merge on GitHub)
git checkout main
git pull origin main
```

### **Sync Fork with Upstream**

```bash
git remote add upstream https://github.com/original/repo.git
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

### **Fix Last Commit**

```bash
# Forgot to add a file?
git add forgotten-file.txt
git commit --amend --no-edit

# Fix commit message?
git commit --amend -m "correct message"
```

### **Undo Last Push**

```bash
# Undo last commit, keep changes
git reset --soft HEAD~1
git commit -m "fixed message"
git push -f  # Only if no one else pulled!
```

---

## 🔍 **Status & Info**

```bash
git status                  # Current status
git log --oneline           # Recent commits
git branch -v               # Branch tracking info
git remote -v               # Remote URLs
git stash list              # Saved stashes
git tag                     # All tags
```

---

## 🚨 **Emergency Commands**

```bash
# "Oh no, I lost my commits!"
git reflog                  # See all commits (history)
git reset --hard SHA        # Recover commit

# "I committed to wrong branch"
git reset --soft HEAD~1     # Undo last commit
git checkout correct-branch
git commit -m "same message"

# "Merge conflict, restart"
git merge --abort
# Start over

# "How do I undo that command?"
git reflog                  # See what you did
git reset --hard @{N}       # Go back N steps
```

---

## 📱 **Mobile/Desktop Apps**

**GitHub Desktop** - Visual Git client
- Clone repositories
- Commit graphically
- No terminal needed

**GitHub Mobile App** - On the go
- View repos
- Review PRs
- Manage notifications

---

## 🎯 **Keyboard Shortcuts (GitHub.com)**

| Key | Action |
|-----|--------|
| `g` `c` | Go to Code tab |
| `g` `i` | Go to Issues |
| `g` `p` | Go to Pull Requests |
| `.` | Open Code Editor (web) |
| `?` | Show all shortcuts |
| `ctrl` `/` | Search |

---

## ✨ **Next Steps**

Learn from: **09-Examples-Explained.md**

See real-world scenarios and walkthroughs!
