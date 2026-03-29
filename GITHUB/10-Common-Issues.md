# 10 - Common Issues & Troubleshooting

## 🆘 **General Error Messages**

### **"fatal: not a git repository"**

**Problem:** You're not in a Git folder

**Solution:**
```bash
# Check if you're in the right folder
pwd

# Initialize Git
git init

# Or clone a repo
git clone <repo-url>
```

---

### **"Please tell me who you are"**

**Problem:** Git doesn't know your name/email

**Solution:**
```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

---

### **"Permission denied (publickey)"**

**Problem:** SSH authentication failing

**Solution 1: Use HTTPS instead**
```bash
git remote set-url origin https://github.com/username/repo.git
```

**Solution 2: Setup SSH properly**
```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your@email.com"

# Copy public key
cat ~/.ssh/id_ed25519.pub

# Add to GitHub: Settings → SSH Keys
# Test connection
ssh -T git@github.com
```

---

### **"The following untracked working tree files..."**

**Problem:** Merge/pull fails due to untracked files

**Solution:**
```bash
# Remove untracked files
git clean -fd

# Or stash your changes
git stash
git pull
git stash pop
```

---

## 📝 **Commit Issues**

### **"Nothing to commit, working tree clean"**

**Problem:** You haven't made changes

**Solution:**
```bash
# Check status
git status

# Make changes to files
# Then add and commit
git add .
git commit -m "message"
```

---

### **"Your branch and 'origin/main' have diverged"**

**Problem:** Remote and local have different commits

**Solution 1: Merge (Keeps both histories)**
```bash
git pull origin main
# Resolve conflicts if any
git push origin main
```

**Solution 2: Rebase (Clean history)**
```bash
git fetch origin
git rebase origin/main
git push origin main
```

---

### **"committed to the wrong branch"**

**Problem:** You committed to main but meant to use feature branch

**Solution:**
```bash
# Undo the commit
git reset --soft HEAD~1

# Switch to correct branch
git checkout feature-branch

# Recommit
git commit -m "same message"

# Push
git push origin feature-branch
```

---

### **"forgot a file in the last commit"**

**Problem:** Need to add a file to the last commit

**Solution:**
```bash
# Add the forgotten file
git add forgotten-file.txt

# Amend the last commit
git commit --amend --no-edit

# If already pushed (be careful!)
git push -f origin branch-name
```

---

### **"need to fix the commit message"**

**Problem:** Commit message has typo or is unclear

**Solution:**
```bash
# Most recent commit
git commit --amend -m "Correct message"

# If already pushed
git push -f origin branch-name

# Older commits (interactive rebase)
git rebase -i HEAD~3  # Last 3 commits
```

---

## 🌳 **Branch Issues**

### **"branch doesn't exist"**

**Problem:** Trying to check out branch that doesn't exist

**Solution:**
```bash
# List all branches
git branch -a

# Create if it doesn't exist
git checkout -b branch-name

# Or fetch from remote first
git fetch origin
git checkout branch-name
```

---

### **"Can't delete branch - not fully merged"**

**Problem:** Trying to delete branch with unmerged commits

**Solution 1: Merge first**
```bash
git checkout main
git merge branch-name
git push
git branch -d branch-name
```

**Solution 2: Force delete (⚠️ careful!)**
```bash
git branch -D branch-name
```

---

### **"created branch but want to rename it"**

**Problem:** Branch name is wrong

**Solution:**
```bash
# Rename locally
git branch -m old-name new-name

# If pushed to remote
git push origin -u new-name
git push origin --delete old-name
```

---

## 🔀 **Merge & Conflict Issues**

### **"Merge conflict - don't know how to resolve"**

**Problem:** Two branches edited same file differently

**Solution:**

1. **Open the conflicted file**

```
<<<<<<< HEAD (main)
def login():
    return "local version"
=======
def login():
    return "feature version"
>>>>>>> feature-branch
```

2. **Choose which to keep**

Option A: Keep local (HEAD)
```python
def login():
    return "local version"
```

Option B: Keep feature
```python
def login():
    return "feature version"
```

Option C: Keep both (merged)
```python
def login(version="both"):
    return "merged version"
```

3. **Complete merge**

```bash
# Remove conflict markers
# Save file

# Add resolved file
git add file.py

# Complete merge
git commit -m "Resolve merge conflict"
```

---

### **"conflict too complex to resolve manually"**

**Problem:** Many conflicts, hard to resolve

**Solution:**
```bash
# Abort merge
git merge --abort

# Try a different approach:
# Either rebase
git rebase main
git rebase --abort  # if too hard

# Or ask teammate for help
```

---

### **"merge created weird history"**

**Problem:** Merge commits making history confusing

**Solution:**
```bash
# Use squash merge next time
git merge --squash feature-branch
git commit -m "Add feature"

# or rebase
git rebase main
```

---

## 🔙 **Undo & Recovery Issues**

### **"accidentally deleted files with git reset"**

**Problem:** Used `git reset --hard` and lost work

**Solution:**
```bash
# View all changes (reflog)
git reflog

# Shows something like:
# abc123e HEAD@{0}: reset: moving to abc123
# def456e HEAD@{1}: commit: your message

# Restore to previous state
git reset --hard def456e

# Check if work is back
git log
```

**Prevention:**
```bash
# Always use soft reset (safer)
git reset --soft HEAD~1  # Keeps your changes
```

---

### **"committed something I shouldn't have"**

**Problem:** Accidentally committed password, secret, etc.

**Solution 1: Not yet pushed**
```bash
# Undo commit
git reset --soft HEAD~1

# Edit files to remove secrets
# Recommit
git commit -m "safe commit"
```

**Solution 2: Already pushed ⚠️**
```bash
# Use BFG Repo Cleaner (recommended)
# See: https://rtyley.github.io/bfg-repo-cleaner/

# Or revert
git revert <commit-hash>

# ALERT your team
# Revoke credentials immediately!
```

---

### **"I lost my commits! Where are they?"**

**Problem:** History seems to have disappeared

**Solution:**
```bash
# Check reflog (keeps history up to 30 days)
git reflog

# Output shows:
# abc123e HEAD@{0}: commit: message1
# def456e HEAD@{1}: commit: message2

# Go back to specific commit
git reset --hard abc123e

# Verify
git log
```

---

## 🌐 **Remote Issues**

### **"can't push - 'origin' doesn't exist"**

**Problem:** Remote not configured

**Solution:**
```bash
# Check remotes
git remote -v

# Add remote
git remote add origin https://github.com/username/repo.git

# Verify
git remote -v

# Try push again
git push -u origin main
```

---

### **"origin points to wrong URL"**

**Problem:** Remote URL is incorrect

**Solution:**
```bash
# Check current URL
git remote -v

# Change it
git remote set-url origin https://github.com/username/newrepo.git

# Verify
git remote -v

# Push again
git push origin main
```

---

### **"too many authentication failures"**

**Problem:** Password authentication failed multiple times

**Solution:**
```bash
# Use GitHub token instead of password
# Generate token at: github.com/settings/tokens
# Use token as password when prompted

# Or setup SSH
# See "Permission denied" section above

# Or cache credentials
git config --global credential.helper store
# Next push will save credentials
```

---

## 📊 **File Tracking Issues**

### **"file keeps appearing as modified but I didn't change it"**

**Problem:** Line endings or permissions changed

**Solution:**
```bash
# Check what changed
git diff filename

# If only whitespace or line endings:
git add filename
git commit -m "Fix line endings"

# Prevent future issues
git config --global core.autocrlf true  # Windows
```

---

### **".gitignore not working - still tracking files"**

**Problem:** Files should be ignored but aren't

**Solution:**
```bash
# Remove from tracking
git rm --cached filename
git commit -m "Remove file from tracking"

# Update .gitignore
echo "filename" >> .gitignore

# Or remove all and re-add
git rm -r --cached .
git add .
git commit -m "Update gitignore"
```

---

### **"need to ignore files I already committed"**

**Problem:** Sensitive files already in repo

**Solution:**
```bash
# UPDATE .gitignore
echo "sensitive-file.txt" >> .gitignore

# Remove from tracking
git rm --cached sensitive-file.txt

# Commit
git commit -m "Remove sensitive file from tracking"

# WARNING: File still in history! 
# Use BFG to remove from entire history if needed
```

---

## 🔍 **Debugging Commands**

### **"What changed in a commit?"**

```bash
git show <commit-hash>
git show --stat <commit-hash>  # Files only
```

### **"When was this line changed?"**

```bash
git blame filename
# Shows who changed each line and when
```

### **"What commits changed this file?"**

```bash
git log filename
git log -p filename  # With details
```

### **"Which branch has this commit?"**

```bash
git branch --contains <commit-hash>
```

---

## 🚨 **Emergency Kill Switch**

### **"Everything is broken, start over!"**

```bash
# Save your changes
git stash

# Delete remote and recreate
# (On GitHub: Delete repo)

# OR delete local and re-clone
cd ..
rm -rf project
git clone https://github.com/username/project.git
cd project
```

---

## 💡 **Prevention Tips**

✅ **Always pull before push**
```bash
git pull
git push
```

✅ **Commit frequently**
- Easier to find bugs
- Easier to recover

✅ **Use branches**
- Main stays stable
- Easier to undo

✅ **Review before committing**
```bash
git diff
git status
```

✅ **Use `.gitignore`**
- Prevent accidents
- Keep repo clean

✅ **Test before pushing**
- Verify code works
- Don't break the build

---

## 📚 **Getting Help**

**Stack Overflow**
- Search your error message
- Check solutions

**GitHub Docs**
- https://docs.github.com
- Comprehensive official docs

**Git Documentation**
- `git help <command>`
- `man git` (Linux/Mac)

**GitHub Community**
- GitHub Discussions
- Stack Overflow

---

## ✨ **Summary**

You now know:
✅ How to install and configure Git  
✅ Basic commands (add, commit, push)  
✅ Branching and merging workflows  
✅ Collaborating with pull requests  
✅ Advanced GitHub features  
✅ Professional best practices  
✅ Real-world examples  
✅ How to troubleshoot problems  

**You're ready to use GitHub like a pro!** 🎉

---

## 🎓 **Next Steps**

1. **Practice** what you learned
2. **Create projects** on GitHub
3. **Contribute** to open-source
4. **Join communities** of developers
5. **Keep learning** - GitHub evolves!

**Good luck, and happy coding!** 🚀
