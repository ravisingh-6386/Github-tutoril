# BONUS - Hands-On Practice Exercises

Ready to practice what you've learned? Here are exercises to reinforce your GitHub skills!

---

## 🎯 **Exercise 1: First Repository (Beginner)**

### **Goal**
Create your first repository on GitHub and push it.

### **Steps**

1. **Create a local folder:**
```bash
mkdir my-first-repo
cd my-first-repo
```

2. **Initialize Git:**
```bash
git init
```

3. **Create files:**
```bash
echo "# My First Repository" > README.md
echo "print('Hello GitHub!')" > hello.py
echo "__pycache__/" > .gitignore
```

4. **Check status:**
```bash
git status
```

5. **Stage files:**
```bash
git add .
```

6. **Commit:**
```bash
git commit -m "Initial commit: add hello script"
```

7. **Create repository on GitHub:**
- Go to github.com
- Click "+" → "New repository"
- Name: `my-first-repo`
- Create

8. **Connect and push:**
```bash
git remote add origin https://github.com/yourusername/my-first-repo.git
git branch -M main
git push -u origin main
```

### **Verify**
- ✅ Repository appears on GitHub
- ✅ Files are visible on GitHub
- ✅ Commit history shows your commit

**Success!** You have your first GitHub repo! 🎉

---

## 🌳 **Exercise 2: Working with Branches (Beginner)**

### **Goal**
Create a feature branch, make changes, and merge back.

### **Setup**
Use the repo from Exercise 1, or clone an existing one.

### **Steps**

1. **Create feature branch:**
```bash
git checkout -b feature/add-greeting
```

2. **Modify `hello.py`:**
```python
def greet(name):
    return f'Hello, {name}!'

if __name__ == '__main__':
    print(greet('GitHub'))
```

3. **Check changes:**
```bash
git diff
```

4. **Stage and commit:**
```bash
git add hello.py
git commit -m "Add greet function for personalized greeting"
```

5. **Push to GitHub:**
```bash
git push -u origin feature/add-greeting
```

6. **Create Pull Request on GitHub:**
- Go to your repo
- You'll see "Compare & pull request"
- Click it
- Add title and description
- Create PR

7. **Merge PR:**
- Click "Merge pull request"
- Confirm merge
- Delete branch

8. **Update local:**
```bash
git checkout main
git pull origin main
git branch -d feature/add-greeting
```

### **Verify**
- ✅ Branch appears on GitHub
- ✅ PR created successfully
- ✅ Code merged to main
- ✅ Changes visible in main branch

**Success!** You mastered the feature branch workflow! 🎯

---

## 🔀 **Exercise 3: Handling Merge Conflicts (Intermediate)**

### **Goal**
Create a merge conflict and resolve it.

### **Steps**

1. **Go to main branch:**
```bash
git checkout main
git pull origin main
```

2. **Create first feature branch:**
```bash
git checkout -b feature/version-a
```

3. **Edit `hello.py` (change first line):**
```python
# Version A
```

4. **Commit and push:**
```bash
git add hello.py
git commit -m "Add version A comment"
git push -u origin feature/version-a
```

5. **Create second feature branch (from main):**
```bash
git checkout main
git checkout -b feature/version-b
```

6. **Edit `hello.py` (change first line differently):**
```python
# Version B - Different comment
```

7. **Commit and push:**
```bash
git add hello.py
git commit -m "Add version B comment"
git push -u origin feature/version-b
```

8. **Merge first branch to main (on GitHub):**
- Go to GitHub
- Create PR for feature/version-a
- Merge it

9. **Try to merge second branch (on GitHub):**
- Create PR for feature/version-b
- Notice "Conflict" message
- Can't merge automatically

10. **Resolve locally:**
```bash
git checkout feature/version-b
git fetch origin
git merge origin/main
```

11. **Edit conflicted file:**
```python
# Resolved - Best of both versions
```

12. **Complete merge:**
```bash
git add hello.py
git commit -m "Resolve merge conflict"
git push origin feature/version-b
```

13. **PR now mergeable - merge on GitHub**

### **Verify**
- ✅ Conflict was triggered
- ✅ You resolved it correctly
- ✅ Both branches merged successfully
- ✅ Final code has your resolution

**Success!** You handled a real merge conflict! 💪

---

## 👥 **Exercise 4: Collaboration Simulation (Intermediate)**

### **Goal**
Simulate team collaboration with two "developers."

### **Setup**
- Clone a repo twice (different folders)
- Simulate two developers

### **Steps**

**Developer A (You - Folder 1):**

1. Create feature:
```bash
git checkout -b feature/sidebar
# Edit files...
git add .
git commit -m "Add sidebar component"
git push -u origin feature/sidebar
```

2. Create PR on GitHub

**Developer B (You - Folder 2):**

1. Fetch latest:
```bash
git fetch origin
git checkout origin/feature/sidebar
git checkout -b feature/sidebar
```

2. Add improvement:
```bash
# Edit files...
git add .
git commit -m "Improve sidebar styling"
git push origin feature/sidebar
```

3. Make comment on PR

**Developer A:**

1. Address feedback:
```bash
git fetch origin
git merge origin/feature/sidebar
# Edit files...
git add .
git commit -m "Address review feedback"
git push origin feature/sidebar
```

2. Approve and merge on GitHub

**Both:**

1. Sync locally:
```bash
git checkout main
git pull origin main
```

### **Verify**
- ✅ Both contributed to same PR
- ✅ Collaborated effectively
- ✅ Code merged successfully
- ✅ Both have latest main branch

**Success!** You simulated real team collaboration! 👥

---

## 🐛 **Exercise 5: Fixing Mistakes (Intermediate)**

### **Goal**
Accidentally commit something and fix it.

### **Steps**

1. **Add a sensitive file (simulated):**
```bash
echo "API_KEY=sk12345" > secret.txt
git add secret.txt
git commit -m "Add secret key" # Oops!
git push
```

2. **Realize mistake:**
```bash
git log --oneline
# See your secret commit
```

3. **Remove from tracking:**
```bash
git rm --cached secret.txt
echo "secret.txt" >> .gitignore
```

4. **Fix commit:**
```bash
git add .gitignore
git commit --amend -m "Initial commit: add project"
```

5. **Force push (only your own branch!):**
```bash
git push -f
```

### **Important Notes**
- ⚠️ Never force push to `main`!
- ⚠️ Never commit secrets in real projects!
- ⚠️ If already public, revoke keys immediately

### **Verify**
- ✅ Sensitive file removed from tracking
- ✅ Commit message fixed
- ✅ `.gitignore` updated

**Success!** You fixed a commit mistake! 🔧

---

## 📚 **Exercise 6: Contributing to Open-Source (Advanced)**

### **Goal**
Contribute to a real open-source project.

### **Steps**

1. **Find a project:**
   - Go to github.com
   - Search for projects with "good-first-issue" label
   - Examples: freeCodeCamp, awesome-python, etc.

2. **Fork the repository:**
   - Click "Fork" button
   - Creates your copy

3. **Clone your fork:**
```bash
git clone https://github.com/yourusername/project.git
cd project
```

4. **Add upstream:**
```bash
git remote add upstream https://github.com/original/project.git
```

5. **Create feature branch:**
```bash
git checkout -b fix/issue-123
```

6. **Make changes:**
   - Follow project guidelines
   - Keep changes focused
   - Add tests if required

7. **Test locally:**
   - Run tests: `npm test`, `pytest`, etc.
   - Verify no errors

8. **Commit and push:**
```bash
git add .
git commit -m "Fix #123: brief description"
git push origin fix/issue-123
```

9. **Create Pull Request:**
   - Go to original repo
   - Click "New Pull Request"
   - Select your fork/branch
   - Fill detailed description
   - Submit

10. **Respond to feedback:**
    - Make requested changes
    - Push updates (PR auto-updates)
    - Be respectful and patient

### **Verify**
- ✅ Fork is current with upstream
- ✅ PR is focused on one issue
- ✅ Tests pass
- ✅ Code follows project style

**Success!** You contributed to open-source! 🌟

---

## 🎓 **Exercise 7: Learning Git History Commands (Advanced)**

### **Goal**
Master advanced git log and search commands.

### **Steps**

1. **View commit history:**
```bash
git log --oneline
git log --graph --all --oneline
```

2. **Search commit messages:**
```bash
git log --grep="fix"
git log --grep="feature" -i
```

3. **See who changed what:**
```bash
git blame filepath.py
```

4. **Find when something was removed:**
```bash
git log -p -- filepath.py
```

5. **See all branches that have a commit:**
```bash
git log --all --oneline | head -20
git branch --contains abc123
```

6. **Find binary search for bug:**
```bash
git bisect start
git bisect bad
git bisect good v1.0.0
# Test each version until found
git bisect reset
```

### **Verify**
- ✅ You can find any commit
- ✅ You understand code history
- ✅ You can track changes over time

**Success!** You mastered Git history! 📚

---

## 🏆 **Final Challenge (Advanced)**

### **Build a Complete Workflow**

Create a project with:

1. **Initial structure:**
   - README.md
   - .gitignore
   - .gitattributes
   - Multiple files

2. **Create multiple features:**
   - feature/auth
   - feature/api
   - feature/database

3. **Create documentation:**
   - Setup guide
   - API reference
   - Contributing guide

4. **Setup automation:**
   - GitHub Actions workflow
   - Auto-run tests
   - Generate reports

5. **Team simulation:**
   - Multiple branches
   - Code reviews
   - Merge conflicts
   - Resolution

6. **Releases:**
   - Tag versions
   - Create releases
   - Write release notes

### **Verify Completion**
- ✅ Professional repository structure
- ✅ Multiple features merged
- ✅ Automated workflows running
- ✅ Releases tagged properly
- ✅ Documentation complete

**Success!** You've mastered GitHub! 🚀

---

## 📝 **Practice Checklist**

Complete exercises in order:

- [ ] Exercise 1: First Repository
- [ ] Exercise 2: Branching
- [ ] Exercise 3: Merge Conflicts
- [ ] Exercise 4: Collaboration
- [ ] Exercise 5: Fixing Mistakes
- [ ] Exercise 6: Open-Source
- [ ] Exercise 7: Git History
- [ ] Challenge: Complete Workflow

---

## 💡 **Tips for Practicing**

✅ **Do exercises multiple times** - Muscle memory helps  
✅ **Try on real projects** - Not just examples  
✅ **Look at others' repos** - Learn from real code  
✅ **Contribute to open-source** - Apply skills  
✅ **Help others** - Teach what you learned  
✅ **Stay consistent** - Practice regularly  
✅ **Make mistakes deliberately** - Best learning  

---

## 🎯 **Next Steps**

1. Complete all exercises in this file
2. Create your own projects
3. Contribute to open-source software
4. Help teammates with GitHub
5. Keep learning new features

---

**Happy practicing, and keep coding!** 🎉
