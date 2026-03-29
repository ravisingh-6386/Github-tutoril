# 04 - Branches & Workflows

## 🌳 **Understanding Branches**

A **branch** is an independent line of development. Think of it as a parallel universe copy of your code.

### **Why Use Branches?**

✅ Keep main code stable  
✅ Work on features independently  
✅ Multiple people can work simultaneously  
✅ Easy to abandon changes  
✅ Clean commit history  

### **Branch Analogy**

```
main branch (STABLE - PRODUCTION):
●—●—●—●—●  (Release 1.0)

feature branch (NEW FEATURE):
    └—●—●—●—┘  (Work in progress)

bugfix branch (QUICK FIX):
    └—●—┘  (Fix & merge back)
```

---

## 📋 **Branch Naming Conventions**

Use clear, descriptive names:

```bash
# Good names
feature/user-authentication
feature/payment-system
bugfix/login-redirect
hotfix/database-crash
docs/setup-instructions
refactor/controller-optimization

# Bad names
feature1
fix-stuff
new-thing
test
update
```

**Pattern:** `type/description`

Types:
- `feature/` - New features
- `bugfix/` - Bug fixes
- `hotfix/` - Urgent production fixes
- `docs/` - Documentation
- `refactor/` - Code restructuring
- `test/` - Testing

---

## 🔀 **Common Branching Strategies**

### **1. Git Flow (Large Teams)**

```
main (PRODUCTION)
  ↑
  ├← release branch
  │
dev (DEVELOPMENT)
  ↑
  ├← feature branches
  ├← bugfix branches
  └← hotfix branches
```

**Main branches:**
- `main` - Production code only
- `dev` - Development/staging

**Support branches:**
- `feature/feature-name` - New features
- `release/version` - Preparing release
- `hotfix/issue` - Emergency fixes

### **2. GitHub Flow (Most Popular)**

```
main (ALWAYS DEPLOYABLE)
  ↑
  ├← feature-1
  ├← feature-2
  ├← bugfix-1
  └← hotfix-1
```

**Single main branch:**
- Always deployable
- Short-lived feature branches
- Merge via pull requests

### **3. Trunk-Based Development (Fast-Paced Teams)**

```
main (ALWAYS SHIPPABLE)
 ↑↑↑ (Frequent commits)
 |||
```

- Developers commit directly or with short-lived branches
- Frequent releases
- CI/CD heavily automated

---

## 🎯 **GitHub Flow Workflow (Recommended for Beginners)**

### **Step 1: Update Main**

```bash
git checkout main
git pull origin main
```

### **Step 2: Create Feature Branch**

```bash
git checkout -b feature/add-search-feature
```

### **Step 3: Make Changes**

```bash
# Edit files
# Test locally
# Verify everything works
```

### **Step 4: Commit Changes**

```bash
git add .
git commit -m "Add search feature to homepage"
```

### **Step 5: Push Branch**

```bash
git push -u origin feature/add-search-feature
```

### **Step 6: Create Pull Request**

1. Go to GitHub repository
2. Click "Pull Requests" tab
3. Click "New Pull Request"
4. Select `main` ← `feature/add-search-feature`
5. Add title and description
6. Click "Create Pull Request"

### **Step 7: Code Review**

- Teammates review
- Suggest changes
- Approve or request changes

### **Step 8: Merge**

1. Once approved, click "Merge Pull Request"
2. Optionally delete remote branch
3. Pull main locally to sync

```bash
git checkout main
git pull origin main
```

---

## 🔄 **Merging Branches**

### **Merge Type 1: Fast-Forward (Linear)**

```
Before:
  main:    ●—●—●
             ↓
  feature:   └—●—●—●

After merge:
  main:    ●—●—●—●—●—●
```

**How:** 
```bash
git checkout main
git merge feature-name
```

### **Merge Type 2: Merge Commit (Preserves History)**

```
Before:
  main:    ●—●—●
             ↙
  feature:   ●—●—●

After:
  main:    ●—●—●—M (Merge commit)
             ↙  ↑
  feature:   ●—●—●
```

**How:**
```bash
git merge --no-ff feature-name
```

---

## 🌊 **Handling Merge Conflicts**

A **conflict** happens when:
- Same line was edited in 2 branches
- Git doesn't know which version to keep

### **Example Conflict**

```
File: app.py

<<<<<<< HEAD (main branch)
def login(username, password):
    # Check database
    return validate_user(username, password)
=======
def login(username, password):
    # Check API
    return api.validate(username, password)
>>>>>>> feature/api-validation
```

### **How to Resolve**

1. **Open conflicted file** in your editor
2. **Choose which version to keep** (or combine both)
3. **Remove conflict markers** (`<<<<<<<`, `=======`, `>>>>>>>`)
4. **Test thoroughly**
5. **Commit merge**

```bash
git add .
git commit -m "Resolve merge conflict in app.py"
```

### **Preventing Conflicts**

✅ Keep branches short-lived  
✅ Communicate with team  
✅ Merge frequently from main  
✅ Pull before pushing  

---

## 🔙 **Reverting to Previous Commits**

### **View Commit History**

```bash
git log --oneline
```

Output:
```
abc123e Feature complete
def456d Fixed typo
7890ghi Initial commit
```

### **Revert Specific Commit**

```bash
git revert abc123e
```

**Creates new commit that undoes changes**

### **Reset to Previous Commit**

```bash
git reset --hard abc123e
```

**⚠️ WARNING:** Deletes all changes after that commit!

---

## 📌 **Stashing Changes**

Sometimes you need to switch branches but have uncommitted changes.

### **Stash Changes**

```bash
git stash
```

**Saves your changes temporarily**

### **Restore Stashed Changes**

```bash
git stash pop           # Restore and remove stash
git stash apply         # Restore but keep stash
```

### **View Stashes**

```bash
git stash list
```

---

## 🌐 **Remote Branch Management**

### **List All Remote Branches**

```bash
git branch -r
```

Output:
```
  origin/main
  origin/feature/search
  origin/bugfix/login
```

### **Track Remote Branch Locally**

```bash
git checkout --track origin/feature/search
# Newer way:
git switch feature/search
```

### **Rename Local Branch**

```bash
git branch -m old-name new-name
```

### **Delete Remote Branch**

```bash
git push origin --delete branch-name
# Or:
git push origin :branch-name
```

---

## 📊 **Viewing Branch Relationships**

### **Visual Branch Graph**

```bash
git log --graph --oneline --all
```

Output:
```
* abc123e Add feature X
|\
| * def456d Fix bug
|/
* 7890ghi Initial commit
```

### **Show Branch Status**

```bash
git status
```

Shows which branch you're on and relationship to remote.

---

## 🎓 **Complete Example: Feature Development**

```bash
# 1. Start from main
git checkout main
git pull

# 2. Create feature branch
git checkout -b feature/dark-mode

# 3. Make changes
# ... edit files ...

# 4. Commit regularly
git add src/theme.css
git commit -m "Add dark mode styles"

git add src/app.js
git commit -m "Add dark mode toggle button"

# 5. Push to GitHub
git push -u origin feature/dark-mode

# 6. Create PR on GitHub (web interface)

# 7. While waiting for review, you can keep working
# Keep branch up to date:
git fetch origin
git merge origin/main
# (resolve any conflicts)
git push

# 8. After approval, go on GitHub and click "Merge Pull Request"

# 9. Delete branch
git branch -d feature/dark-mode
git push origin --delete feature/dark-mode

# 10. Back to main
git checkout main
git pull
```

---

## ✨ **Next Steps**

Learn about: **05-Collaboration.md**

You'll learn how to work with others using Pull Requests, Issues, and Forks!
