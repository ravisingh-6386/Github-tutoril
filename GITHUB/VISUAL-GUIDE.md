# BONUS - Visual Git Workflow Guide

## 🎨 **Visual Workflows**

### **1. Basic Daily Workflow**

```
START YOUR DAY
    ↓
git checkout main
    ↓
git pull origin main
    ↓
Create feature branch
    ↓
git checkout -b feature/task
    ↓
MAKE CHANGES
    ↓
git add .
    ↓
git commit -m "message"
    ↓
git push origin feature/task
    ↓
CREATE PULL REQUEST
    ↓
CODE REVIEW (on GitHub)
    ↓
MERGE (on GitHub)
    ↓
git checkout main
    ↓
git pull origin main
    ↓
CONTINUE TO NEXT TASK
```

---

### **2. Feature Branch Lifecycle**

```
main branch:   M1 ——— M2 ——— M3 ——— M4 ——— M5 (merged)
                ↓                      ↑
feature branch: └── F1 ── F2 ── F3 ──┘
                (creation)  (work)  (merge)

Legend:
M = Commit on main
F = Commit on feature branch
```

---

### **3. Merge Conflict Resolution**

```
Your Changes          Original            Their Changes
(HEAD)                (main)              (their branch)
    ↓                  ↓                       ↓
function() {      function() {          function() {
  return "A"  ?     return ??           return "B"
}                 }                     }
    ↓                  ↑                       ↑
    └─── CONFLICT ────┘
    
Resolve by:
  ❌ Keep yours ONLY
  ❌ Keep theirs ONLY
  ✅ Combine both
  ✅ Keep best of both
  ✅ Refactor completely
```

---

### **4. Rebase vs Merge**

```
MERGE (Preserves History)
─────────────────────────
Before:   main → C1 → C2
             ↘
              feature → C3 → C4

After:    main → C1 → C2 → M(merge) → (C3 + C4)
             ↖──────────────────────↗

REBASE (Linear History)
──────────────────────
Before:   main → C1 → C2
             ↘
              feature → C3 → C4

After:    main → C1 → C2 → C3 → C4
```

---

### **5. Remote Workflow**

```
Local Computer                GitHub (Remote)
┌──────────────┐             ┌──────────────┐
│   Repository │             │  Repository  │
│   (git init) │             │  (github.com)│
└──────┬───────┘             └──────┬───────┘
       │                            │
       │ git add + commit           │
       │──────────────→ (local)     │
       │                            │
       │ git push                   │
       │───────────────────────────→│
       │                            │
       │ git pull ↓                 │
       │←───────────────────────────│
       │         (fetch + merge)    │
       │                            │
```

---

### **6. Pull Request Process**

```
1. CREATE
   ├─ Push branch to GitHub
   ├─ Click "Compare & pull request"
   └─ Fill in description

2. REVIEW
   ├─ Team reviews code
   ├─ Add comments
   └─ Request changes (optional)

3. RESPOND
   ├─ Review feedback
   ├─ Make changes locally
   ├─ Commit updates
   └─ Push (PR auto-updates)

4. APPROVE
   ├─ Reviewer approves
   └─ PR shows "Ready to merge"

5. MERGE
   ├─ Click "Merge Pull Request"
   ├─ Delete remote branch
   └─ Pull latest locally

6. CLEANUP
   ├─ Delete local branch
   └─ Continue to next task
```

---

### **7. Git State Transitions**

```
                    ┌─────────────────┐
                    │  Unmodified     │
                    │  (in repo)      │
                    └────────▲────────┘
                             │
                             │ git remove
                             │
                  ┌──────────┴──────────┐
                  ↓                     ↓
           ┌──────────────┐      ┌──────────────┐
           │  Modified    │      │  Untracked   │
           │  (changed)   │      │  (new file)  │
           └──────┬───────┘      └──────┬───────┘
                  │                     │
                  │ git add             │ git add
                  │                     │
                  └──────────┬──────────┘
                             ↓
                    ┌─────────────────┐
                    │    Staged       │
                    │  (ready to      │
                    │   commit)       │
                    └────────┬────────┘
                             │
                             │ git reset
                             │
                             ↓
                    ┌─────────────────┐
                    │    Committed    │
                    │   (in repo)     │
                    └────────┬────────┘
                             │
                             │ git push
                             ↓
                    ┌─────────────────┐
                    │    Pushed       │
                    │  (on GitHub)    │
                    └─────────────────┘
```

---

## 📊 **Command Decision Tree**

```
What do you want to do?

├─ VIEW INFORMATION
│  ├─ git status ................ Current state
│  ├─ git log ................... Commit history
│  ├─ git diff .................. What changed
│  └─ git show <commit> ......... Commit details
│
├─ MAKE CHANGES
│  ├─ git add . ................. Stage all
│  ├─ git add <file> ............ Stage specific
│  └─ git commit -m "msg" ....... Save changes
│
├─ WORK WITH BRANCHES
│  ├─ git branch ................ List branches
│  ├─ git checkout -b <name> .... Create branch
│  ├─ git checkout <name> ....... Switch branch
│  ├─ git merge <name> .......... Merge branch
│  └─ git branch -d <name> ...... Delete branch
│
├─ SYNC WITH REMOTE
│  ├─ git fetch ................. Download only
│  ├─ git pull .................. Download + merge
│  ├─ git push .................. Upload
│  └─ git push origin --delete .. Delete remote
│
├─ UNDO CHANGES
│  ├─ git restore <file> ........ Discard changes
│  ├─ git reset --soft HEAD~1 ... Undo (keep work)
│  ├─ git reset --hard HEAD~1 ... Undo (discard)
│  └─ git revert <commit> ....... Create undo commit
│
└─ EMERGENCY
   ├─ git reflog ................ See all history
   ├─ git reset --hard <ref> .... Recover
   └─ git merge --abort ......... Cancel merge
```

---

## 🎯 **Git Workflow Comparison**

```
SIMPLE WORKFLOW (Solo)
──────────────────────
main → feature → edit → commit → push → PR → merge

GIT FLOW (Large Teams)
──────────────────────
main  ← release ← dev ← feature
       ← hotfix ↑

TRUNK-BASED (Fast-Paced)
─────────────────────────
main ← short branches (1-2 days)
    ↑ frequent commits & deploys
```

---

## 📝 **Commit History Examples**

### **Good History (Clean)**
```
abc123 Fix login validation bug
def456 Add user authentication
7890gh Add database connection
ij1234 Initial project setup
```

### **Bad History (Messy)**
```
abc123 WIP
def456 fix
7890gh more fixes
ij1234 finally working
kl5678 oops
mn6789 typo
```

### **After Squashing Bad History**
```
abc123 Add user authentication with database and login
def456 Initial project setup
```

---

## 🔄 **Common Git Scenarios**

### **"I need to update my branch with main"**

```
Option 1 (MERGE - Adds merge commit)
──────────────────────────────────
git checkout my-feature
git fetch origin
git merge origin/main
                        ↓
                (creates merge commit)

Option 2 (REBASE - Clean history)
──────────────────────────────────
git checkout my-feature
git fetch origin
git rebase origin/main
                        ↓
                (replays commits cleanly)
```

### **"I committed to wrong branch"**

```
Current State: main has bad commit
             feature branch empty

Solution:
git reset --soft HEAD~1     (commit → staged changes)
git checkout feature-branch
git commit -m "message"     (commit to correct branch)
git push feature-branch
```

### **"I want to undo last 3 commits"**

```
Option 1: Soft reset (keep changes)
──────────────────────────────────
git reset --soft HEAD~3
(changes go back to staged)

Option 2: Hard reset (discard)
────────────────────────────
git reset --hard HEAD~3
(⚠️ Changes are lost!)

Option 3: Revert (create undo commits)
──────────────────────────────────────
git revert HEAD~2..HEAD
(creates 3 new commits undoing them)
```

---

## 🎓 **Learning Path Map**

```
START HERE
    ↓
[Git Basics]
├─ What is Git?
├─ Installation
└─ Configuration
    ↓
[Core Commands]
├─ Add, Commit, Push
├─ Pull, Clone
└─ Log, Status
    ↓
[Branches & Merging]
├─ Create branches
├─ Merge branches
└─ Handle conflicts
    ↓
[Collaboration]
├─ Pull Requests
├─ Code Review
└─ Issues
    ↓
[Advanced Features]
├─ GitHub Actions
├─ Projects
└─ Releases
    ↓
[Best Practices]
├─ Commit messages
├─ Branching strategy
└─ Team workflow
    ↓
[Open-Source]
├─ Forking
├─ Contributing
└─ Community
    ↓
EXPERT LEVEL ✨
```

---

## ⚡ **Pro Tips**

### **Command Aliases**
```bash
git config --global alias.st status
git config --global alias.br branch
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.unstage 'restore --staged'

# Now use: git st, git br, git co, etc.
```

### **Useful Git Config**
```bash
# Show branch in terminal
git config --global color.ui true

# Set editor
git config --global core.editor "code --wait"

# Default branch name
git config --global init.defaultBranch main

# Sign commits
git config --global user.signingkey <GPG-KEY>
git config --global commit.gpgsign true
```

### **Terminal Tricks**
```bash
# See branch in bash prompt
# Add to ~/.bashrc or ~/.zshrc
export PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w$(__git_ps1 " (%s)")\$ '
```

---

## 🎯 **Quick Reference**

| Need | Command |
|------|---------|
| **Check status** | `git status` |
| **Create branch** | `git checkout -b name` |
| **Stage changes** | `git add .` |
| **Commit** | `git commit -m "msg"` |
| **Push** | `git push origin branch` |
| **Pull** | `git pull` |
| **Merge** | `git merge branch` |
| **View history** | `git log --oneline` |
| **See changes** | `git diff` |
| **Undo file** | `git restore file` |
| **Undo commit** | `git reset --soft HEAD~1` |
| **View branches** | `git branch -a` |

---

**Print this page for quick reference during work!** 📌

---

## 🎉 **Mastery Checklist**

- [ ] Understand Git fundamentals
- [ ] Can create and manage repositories
- [ ] Comfortable with branches and merging
- [ ] Can resolve merge conflicts
- [ ] Understand pull requests
- [ ] Can contribute to open-source
- [ ] Know best practices
- [ ] Can troubleshoot common issues
- [ ] Familiar with GitHub Actions
- [ ] Help others with Git/GitHub

**Once you've checked all boxes, you're a GitHub master!** 🏆
