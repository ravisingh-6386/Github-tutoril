# 07 - Best Practices & Professional Workflows

## 📋 **Commit Best Practices**

### **Golden Rules**

1. **Commit often** - Multiple small commits vs one large commit
2. **Write clear messages** - Others (and future you) will read them
3. **One logical change per commit** - Easier to review and revert
4. **Test before committing** - Don't break the build

### **Commit Message Guidelines**

**Format:**
```
<type>: <subject>

<body>

<footer>
```

**Example:**
```
feat: Add user authentication

Implement JWT-based authentication system with:
- Login endpoint
- Token refresh mechanism
- Session validation

This closes #123
```

**Types:**
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation
- `style:` - Code style (no logic change)
- `refactor:` - Code restructuring
- `perf:` - Performance improvement
- `test:` - Adding/updating tests
- `chore:` - Maintenance tasks

### **Bad Commits to Avoid**

```bash
# ❌ Too vague
git commit -m "updates"
git commit -m "fixes"
git commit -m "stuff"

# ❌ Too large
git commit -m "Add authentication, update database schema, fix UI bugs, update docs"

# ❌ Multiple changes
git commit -m "Add feature and remove deprecated code"
```

### **Good Commits**

```bash
# ✅ Specific and clear
git commit -m "Add password reset email verification"
git commit -m "Fix null pointer exception in user service"
git commit -m "Update README with installation instructions"

# ✅ One change per commit
```

---

## 🌳 **Branching Best Practices**

✅ **Branch from main** - Always base on latest main  
✅ **Short-lived branches** - Delete after merge (days, not months)  
✅ **Descriptive names** - `feature/add-search` not `feature1`  
✅ **One feature per branch** - Keep responsibility clear  
✅ **Sync with main regularly** - Don't fall too far behind  

### **Before Starting Work**

```bash
git checkout main
git pull origin main
git checkout -b feature/your-feature-name
```

### **While Working**

Keep updated:
```bash
# Every few days
git fetch origin
git merge origin/main
```

Or rebase (preferred by some):
```bash
git fetch origin
git rebase origin/main
```

### **After Code Review**

Delete local branch:
```bash
git branch -d feature-name
```

Delete remote:
```bash
git push origin --delete feature-name
```

---

## 🔄 **Pull Request Best Practices**

### **Before Creating PR**

✅ Run tests locally  
✅ Check code style  
✅ Update documentation  
✅ Add tests for new code  
✅ Remove debug code  
✅ Small and focused (max ~400 lines)  

### **PR Description**

```markdown
## What does this PR do?
Brief description of changes.

## Why are these changes needed?
What problem does it solve?

## Testing
How was this tested?

## Related Issues
Closes #123

## Checklist
- [x] Tests pass
- [x] No breaking changes
- [x] Documentation updated
```

### **Responding to Reviews**

✅ **Be gracious** - Reviewers are helping  
✅ **Ask for clarification** - If feedback is unclear  
✅ **Don't argue** - Discuss technical merits  
✅ **Update PR quickly** - Don't let it sit  
✅ **Thank reviewers** - Acknowledge their time  

❌ **Don't:**
```
"This is fine, accept it"
"I disagree, merge anyway"
"Your review doesn't matter"
```

✅ **Do:**
```
"Good catch! I'll fix that."
"Can you clarify what you mean?"
"I see your point, let's discuss."
```

---

## 🧪 **Testing Best Practices**

### **Write Tests**

```bash
# For every feature
# At least cover happy path

# Example Python test
def test_login_valid_credentials():
    result = login("user@example.com", "password123")
    assert result.success == True
    assert result.user_id == 123

def test_login_invalid_password():
    result = login("user@example.com", "wrong")
    assert result.success == False
```

### **Test Before Push**

```bash
# Run locally
npm test
pytest
./gradlew test

# Commit only if passing
git add .
git commit -m "Add login tests"
```

### **Continuous Integration**

Automate testing:
```yaml
# .github/workflows/tests.yml
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm install
      - run: npm test
```

---

## 📚 **Documentation Best Practices**

### **README is Essential**

Every repo should have `README.md`:

```markdown
# Project Name

Brief description of what this project does.

## Features
- Feature 1
- Feature 2

## Installation
Step-by-step instructions

## Usage
Code examples showing how to use

## Contributing
How to contribute (if open-source)

## License
Which license?
```

### **Inline Comments**

Good comments explain **why**, not **what**:

```python
# ❌ Bad - explains what code does
x = y * 2  # multiply y by 2

# ✅ Good - explains why
# Double the width to account for padding
x = y * 2
```

### **Keep Docs Updated**

- Update docs when changing code
- Add docs for new features
- Remove docs for deprecated features

---

## 👥 **Team Collaboration**

### **Code Review Process**

1. **Create PR** with clear description
2. **Request reviewers** (2+ for critical code)
3. **Address feedback** professionally
4. **Approval** from reviewers
5. **Merge** when ready
6. **Delete branch** after merge

### **Communication**

✅ Be clear and concise  
✅ Ask questions if unclear  
✅ Give context in comments  
✅ Use mentions: `@username` for important  
✅ Respect team members' time  

### **Code Ownership**

```yaml
# CODEOWNERS file
# Everyone owns these files
*  @user1  @user2

# Backend team owns src/api
/src/api/  @backend-team

# Frontend team owns src/ui  
/src/ui/  @frontend-team
```

---

## 🔄 **Merge Strategies**

### **Squash & Merge**

All commits become one:
```
Before: c1 — c2 — c3
After:  [squashed commit]
```

**Good for:** Small features, keeping history clean

### **Rebase & Merge**

Replays commits on top:
```
Before:   main — c1 — c2
After:         — c1 — c2
```

**Good for:** Linear history, easier to understand

### **Create Merge Commit**

Preserves all history:
```
Before: main ← feature
After:  main —M— (merge commit includes both)
```

**Good for:** Complex histories, easy to revert

---

## 🚫 **What NOT to Do**

❌ **Commit to main directly**
```bash
# Don't do this
git checkout main
git add .
git commit -m "quick fix"
```

❌ **Force push to main**
```bash
git push -f  # NEVER on main!
```

❌ **Large, unclear commits**
```bash
git commit -m "stuff"  # What does this do??
```

❌ **Commit secrets/passwords**
```yaml
# Don't commit
api_key: "sk-12345"
password: "mypassword"
```

❌ **Break the build**
```bash
# Test before pushing
git push  # ❌ Broken tests
```

---

## 🎯 **Daily Workflow**

### **Start of Day**

```bash
git checkout main
git pull origin main
```

### **During Development**

```bash
# Work on feature branch
git checkout -b feature/task

# Make changes, commit frequently
git add .
git commit -m "progress message"

# Keep in sync
git fetch origin
git merge origin/main
```

### **Submit for Review**

```bash
git push -u origin feature/task
# Create PR on GitHub
```

### **After Approval**

```bash
# Merge on GitHub (web interface)

# Sync locally
git checkout main
git pull origin main
git branch -d feature/task
```

---

## 🏆 **GitHub Profile Tips**

✅ Pin important repositories  
✅ Add README to profile  
✅ Keep contributions consistent  
✅ Contribute to open-source  
✅ Share and star interesting projects  

### **Profile README**

Create `README.md` in new repo: `username/username`

```markdown
# Hi there 👋

- 👀 I'm interested in Python and React
- 🔭 I'm working on open-source projects
- 📫 How to reach me: email@example.com
- ⚡ Fun fact: I love hiking
```

---

## ✨ **Next Steps**

Learn: **08-Git-Cheat-Sheet.md**

Get quick reference for common commands!
