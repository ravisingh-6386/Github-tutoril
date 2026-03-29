# 01 - What is GitHub?

## 🌐 **The Basics**

### **Git vs GitHub**

| Git | GitHub |
|-----|--------|
| **Version control system** | **Cloud platform for Git** |
| Runs on your computer | Hosted on the internet |
| Tracks code changes | Hosts repositories + collaboration |
| Command-line tool | Website + desktop apps |
| Free software | Free + paid plans |

---

## 🎯 **What is GitHub?**

GitHub is a **website** where developers:
- Store code online
- Collaborate with others
- Track changes and history
- Manage projects
- Share code with the world

Think of it like **Google Drive for code**.

---

## 🏗️ **Key Components**

### **1. Repository (Repo)**
A folder containing:
- Your project files
- Complete version history
- Configuration files
- Documentation

**Two types:**
- **Public** - Anyone can see (ideal for open-source)
- **Private** - Only invited people can see (ideal for work/personal)

### **2. Commits**
- Snapshots of your code at a point in time
- Include a message describing changes
- Create an audit trail
- Allow you to revert if needed

```
Commit history looks like:
    [Initial setup]
         ↓
    [Add login feature]
         ↓
    [Fix login bug]
         ↓
    [Current state]
```

### **3. Branches**
- Separate "copies" of your code
- Work independently without affecting main code
- `main` branch = production-ready code
- Feature branches = new features being developed

```
main branch:    ●——●——●——●
                 ↑
feature branch:   └—●—●—┘
                 (parallel work)
```

### **4. Remote**
- Your repository hosted on GitHub
- `origin` = your main remote repository
- `upstream` = original repository (if you forked)

### **5. Pull Requests (PR)**
- Proposal to merge changes
- Code review happens here
- Discussion and feedback
- Once approved, changes merge into main

---

## 🔄 **Basic Workflow**

```
1. Clone repo  →  2. Create branch  →  3. Make changes
                                            ↓
6. Merge approved  ←  5. Code review  ←  4. Push & create PR
```

---

## 💻 **How It Works - Flow Diagram**

```
Your Computer (Local)          GitHub (Remote)
     ┌─────────────┐              ┌──────────────┐
     │   Git Repo  │              │  Repository  │
     │  (Folders)  │              │   (Online)   │
     └────────┬────┘              └──────┬───────┘
              │                          │
       git push ────────────────────────→│
              │                          │
              │ ←───────── git pull ────│
              │                          │
```

---

## 📊 **Repository Structure**

```
my-project/
├── README.md           (Project description)
├── .gitignore          (Files to ignore)
├── LICENSE             (Legal terms)
├── src/                (Source code)
│   ├── main.py
│   └── utils.py
├── tests/              (Test files)
│   └── test_main.py
├── docs/               (Documentation)
│   └── setup.md
└── .github/            (GitHub specific)
    └── workflows/      (Actions/automation)
```

---

## 👥 **Collaboration Features**

### **Forks**
- Create your own copy of someone's repo
- Make changes independently
- Contribute back via Pull Requests
- Common in open-source

### **Issues**
- Track bugs and feature requests
- Assign to team members
- Add labels and milestones
- Link to pull requests

### **Discussions**
- Q&A and general conversation
- Lighter than issues
- Community engagement

### **Projects**
- Task management (Kanban boards)
- Visual workflow tracking
- Organize issues and PRs

---

## 🚀 **Why Use GitHub?**

✅ **Backup** - Code safely stored online  
✅ **Collaboration** - Work with teammates  
✅ **History** - See all changes over time  
✅ **Recovery** - Revert to previous versions  
✅ **Open Source** - Share code with world  
✅ **Portfolio** - Show your work to employers  
✅ **Free** - No cost for basic features  
✅ **Community** - Network with developers  

---

## 🎓 **Common Terms**

| Term | Meaning |
|------|---------|
| **Clone** | Copy repo to your computer |
| **Add** | Stage files for commit |
| **Commit** | Save changes with message |
| **Push** | Upload to GitHub |
| **Pull** | Download changes |
| **Merge** | Combine branches |
| **Branch** | Separate line of development |
| **Fork** | Copy someone's repo |
| **PR** | Request to merge changes |
| **Diff** | Difference between versions |

---

## 🌟 **Real-World Example**

```
Developer A (You)          GitHub             Developer B (Teammate)
    ↓                         ↓                       ↓
1. Clone shared repo
2. Create branch "feature"
3. Make changes
4. Commit locally
5. Push to GitHub
                          6. B sees your PR
                          7. Reviews your code
                    ←─────────────────→
8. B suggests changes
                          9. You make updates
                          10. Push again
                    ←─────────────────→
                          11. B approves
                          12. Merge PR
    ↓                         ↓                       ↓
13. Pull latest version  ← [featurebranch merged]  14. Pull latest version
```

---

## 📚 **Next Steps**

Now that you understand the basics, let's move to: **02-Installing-Git.md**

In the next file, you'll learn how to install and configure Git on your computer.
