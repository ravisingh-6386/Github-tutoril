# 05 - Collaboration Features

## 🤝 **Pull Requests (PR)**

A **Pull Request** is a proposal to merge changes into another branch (usually main).

### **Why Pull Requests?**

✅ **Code Review** - Others review before merge  
✅ **Discussion** - Talk about changes  
✅ **Quality Gate** - Catch bugs early  
✅ **Documentation** - Record decisions  
✅ **Automation** - Run tests automatically  

### **Pull Request Lifecycle**

```
1. Create PR
   ↓
2. Add description
   ↓
3. Run automated tests
   ↓
4. Request reviewers
   ↓
5. Receive feedback
   ↓
6. Make changes (if needed)
   ↓
7. Approval (✅)
   ↓
8. Merge to main
```

### **Creating a Pull Request**

**Command line:**

```bash
# Make changes on feature branch
git add .
git commit -m "Add search feature"
git push -u origin feature/search
```

**Then on GitHub.com:**

1. Go to your repository
2. Click "Pull Requests" tab
3. Click "New Pull Request"
4. Select branches:
   - **Base:** main (where you want changes)
   - **Compare:** feature/search (your changes)
5. Review changes shown
6. Click "Create Pull Request"
7. Fill in title and description

### **Pull Request Description Template**

```markdown
## Description
Brief description of what this PR does.

## Changes
- Added search input field
- Implemented search algorithm
- Added test cases

## Related Issues
Closes #123

## Type of Change
- [x] New feature
- [ ] Bug fix
- [ ] Breaking change

## Testing
How was this tested?
- Manual testing on homepage
- Unit tests passing
- Browser compatibility checked

## Screenshots (if applicable)
[Before/After screenshots]

## Checklist
- [x] Code follows style guidelines
- [x] Comments added for complex logic
- [x] Tests updated
- [x] Documentation updated
```

### **Reviewing a Pull Request**

**As a Reviewer:**

1. Review "Files changed" tab
2. Click "Review changes" button at top-right
3. Add comments:
   - **Comment:** Suggestion (non-blocking)
   - **Approve:** Good to merge
   - **Request changes:** Must fix before merge
4. Submit review

**Comment on specific lines:**
- Hover over line number
- Click "+" button
- Type comment
- Click "Reply"

---

## 🔄 **Forks: Open-Source Contribution**

A **fork** is your personal copy of someone else's repository.

### **Why Fork?**

- Don't have write access to original repo
- Want to contribute to open-source
- Want to start your own version

### **Forking Workflow**

```
Original Repository (upstream)
         ↓ (fork)
Your Fork (origin)
         ↓ (clone)
Your Computer (local)
```

### **Steps to Contribute via Fork**

**Step 1: Fork Repository**
1. Go to https://github.com/original-owner/project
2. Click "Fork" button (top-right)
3. Creates copy at https://github.com/yourname/project

**Step 2: Clone Your Fork**

```bash
git clone https://github.com/yourname/project.git
cd project
```

**Step 3: Add Upstream Remote**

```bash
git remote add upstream https://github.com/original-owner/project.git
git remote -v
```

Shows:
```
origin    https://github.com/yourname/project.git (fetch)
origin    https://github.com/yourname/project.git (push)
upstream  https://github.com/original-owner/project.git (fetch)
upstream  https://github.com/original-owner/project.git (push)
```

**Step 4: Keep Fork Updated**

```bash
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

**Step 5: Create Feature Branch**

```bash
git checkout -b feature/your-contribution
# ... make changes ...
git add .
git commit -m "Add awesome feature"
git push origin feature/your-contribution
```

**Step 6: Create Pull Request**
1. Go to original repository on GitHub
2. Click "Pull Requests" → "New Pull Request"
3. Click "compare across forks"
4. Select:
   - base: upstream/main (original repo)
   - compare: yourname:feature/your-contribution
5. Click "Create Pull Request"
6. Fill in description
7. Submit!

**Step 7: Address Feedback**

```bash
# Make requested changes
git add .
git commit -m "Address review feedback"
git push origin feature/your-contribution
# PR automatically updates
```

---

## 🐛 **Issues: Bug & Feature Tracking**

An **issue** is a way to track bugs, features, questions, and tasks.

### **Creating an Issue**

1. Go to repository
2. Click "Issues" tab
3. Click "New issue"
4. Add:
   - **Title:** Clear description (max ~50 chars)
   - **Description:** Details, steps to reproduce, expected behavior
   - **Labels:** bug, feature, documentation, etc.
   - **Assignee:** Who's working on it?
   - **Milestone:** Release version

### **Issue Template**

**For Bug Reports:**
```markdown
## Description
Brief description of the bug.

## Steps to Reproduce
1. Go to '...'
2. Click on '...'
3. See error

## Expected Behavior
What should happen?

## Actual Behavior
What actually happened?

## Environment
- OS: macOS 12.1
- Browser: Chrome 98
- Version: 1.2.3

## Screenshots
[Include if applicable]
```

**For Feature Requests:**
```markdown
## Description
What feature should be added?

## Use Case
Who needs this? Why?

## Proposed Solution
How should it work?

## Alternatives Considered
Other approaches?
```

### **Issue Linking**

**Link Issue to PR:**
```markdown
Closes #123
Fixes #456
Related to #789
```

When you merge PR, issues automatically close!

### **Comments on Issues**

- Discuss solutions
- Share information
- Tag people: `@username mention`
- Add reactions: 👍 ❤️ 😄

---

## 👥 **Teams & Permissions**

### **Repository Roles**

| Role | Permissions |
|------|-------------|
| **Owner** | Full control, delete repo |
| **Admin** | Manage settings, add collaborators |
| **Write** | Push, merge, delete branches |
| **Triage** | Manage issues & PRs, no code push |
| **Read** | View only, no push |

### **Adding Collaborators**

1. Go to repository Settings
2. Click "Collaborators"
3. Click "Add people"
4. Search for username
5. Select permission level
6. Send invitation

---

## 💬 **Discussions**

**Discussions** are lighter than Issues - good for:
- Questions
- Announcements
- General conversation
- Decisions

1. Go to **Discussions** tab
2. Click **New discussion**
3. Choose category:
   - Announcements
   - General
   - Ideas
   - Polls
   - Q&A
4. Post your discussion

---

## 🏆 **Code Review Best Practices**

### **As a Reviewer:**

✅ **Be respectful** - It's code, not personal  
✅ **Ask questions** - Don't demand changes  
✅ **Suggest improvements** - Not requirements  
✅ **Test locally** - Run the code  
✅ **Check tests** - Are there tests?  
✅ **Look for bugs** - Security, performance, logic  
✅ **Be timely** - Review within 24 hours  

### **As an Author:**

✅ **Keep PR small** - Easier to review  
✅ **Good descriptions** - Explain context  
✅ **Respond professionally** - Thank reviewers  
✅ **Ask questions** - If feedback is unclear  
✅ **Test before submitting** - Verify it works  

---

## 📋 **Common Issue & PR Labels**

```
bug            - Something isn't working
enhancement    - New feature
documentation  - Improve docs
good-first-issue - Good for newcomers
help-wanted    - Need assistance
wontfix        - Won't be fixed
duplicate      - Already reported
invalid        - Not a real issue
question       - Needs clarification
```

---

## 🔔 **Notifications**

You'll get notified when:
- Someone mentions you: `@username`
- Assigns you issue/PR
- Requests your review
- Comments on your PR
- Your PR is merged

**Manage notifications:**
1. Click profile icon (top-right)
2. Click "Settings"
3. Go to "Notifications"
4. Configure email & web preferences

---

## ✨ **Next Steps**

Learn about: **06-Advanced-Features.md**

You'll learn GitHub Actions, Projects, Releases, and more!
