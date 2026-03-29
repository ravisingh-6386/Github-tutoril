# 06 - Advanced GitHub Features

## ⚙️ **GitHub Actions (CI/CD)**

**GitHub Actions** automates tasks when events happen in your repository.

### **What Can You Automate?**

✅ Run tests on every push  
✅ Deploy to production  
✅ Build Docker images  
✅ Notify team members  
✅ Lint code  
✅ Update dependencies  
✅ Generate reports  

### **Workflow Example: Automated Tests**

Create file: `.github/workflows/tests.yml`

```yaml
name: Run Tests

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v3
      
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.10'
      
      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt
      
      - name: Run tests
        run: pytest
```

**What this does:**
1. Triggers on push or PR creation
2. Starts on Ubuntu machine
3. Checks out code
4. Installs Python
5. Installs dependencies
6. Runs pytest

### **View Workflow Status**

1. Go to repository
2. Click "Actions" tab
3. See workflow run history
4. Click run to see details

### **Common Workflows**

**Deploy on Release:**
```yaml
on:
  release:
    types: [published]
```

**Schedule (Nightly Builds):**
```yaml
on:
  schedule:
    - cron: '0 2 * * *'  # 2 AM daily
```

**Manual Trigger:**
```yaml
on: workflow_dispatch
```

---

## 📊 **Project Boards**

**Project Boards** help organize work using Kanban-style workflow.

### **Creating a Project**

1. Go to repository
2. Click "Projects" tab
3. Click "New project"
4. Choose template:
   - **Basic:** Custom columns
   - **Table:** Spreadsheet view
   - **Roadmap:** Timeline view

### **Kanban Board Example**

```
To Do          In Progress      Done
├─ Issue #1    ├─ Issue #3      ├─ Issue #2
├─ Issue #4    └─ Issue #5      └─ Issue #6
└─ Issue #7
```

### **Using Automation**

Set rules to auto-move cards:
- Move to "In Progress" when PR created
- Move to "Done" when PR merged
- Auto-add new issues to "To Do"

### **Organization-Level Projects**

Create board for entire organization:
1. Go to organization
2. Click "Projects" tab
3. Create board for multiple repositories

---

## 🏷️ **Releases**

A **Release** marks a version of your software.

### **Creating a Release**

1. Go to repository
2. Click "Releases" (right sidebar)
3. Click "Create a new release"
4. Fill in:
   - **Tag:** version number (v1.0.0)
   - **Release title:** Human-readable name
   - **Description:** What changed?
   - **Attachments:** Upload binaries (optional)
5. Publish release

### **Release Notes Template**

```markdown
## Version 1.2.0

### New Features
- Added dark mode toggle
- Implemented search functionality

### Bug Fixes
- Fixed login redirect issue
- Fixed memory leak in background worker

### Breaking Changes
- Changed API endpoint /api/v1 to /api/v2

### Installation
Download from releases or use package manager:
```bash
npm install my-package@1.2.0
```

**Thank you to contributors:**
@username1, @username2

---

## 📚 **Wiki**

A **Wiki** is documentation for your project.

### **Accessing Wiki**

1. Go to repository
2. Click "Wiki" tab
3. Create pages:
   - Home
   - Getting Started
   - API Documentation
   - Troubleshooting

### **Wiki Example**

**Home:**
```markdown
# My Project

This is the main documentation hub.

## Pages
- [Getting Started](Getting-Started)
- [API docs](API-Reference)
- [FAQ](FAQ)
```

**Getting Started:**
```markdown
# Getting Started

## Installation

1. Clone the repo
1. Install dependencies
1. Run the project

## Basic Usage

### Example Code
\`\`\`python
from myproject import main
main()
\`\`\`
```

---

## 🔍 **Search & Insights**

### **Code Search**

**Search across entire repository:**
1. Click search icon (top-center)
2. Type query
3. Filter by file type, language, etc.

**Advanced search syntax:**
```
language:python              # Python files only
filename:README              # Find README
path:src/                    # In src folder
user:torvalds                # By specific user
created:2023-01-01..2024    # Date range
```

### **Repository Insights**

1. Go to "Insights" tab
2. View:
   - **Traffic:** Visitors and clones
   - **Forks:** Network of forks
   - **Members:** List of contributors
   - **Contributors:** Commit statistics
   - **Community:** Health check

---

## 🔐 **Dependabot**

**Dependabot** automatically updates dependencies with security fixes.

### **Enabling Dependabot**

1. Go to Settings
2. Click "Security & analysis"
3. Enable "Dependabot alerts"
4. Enable "Dependabot security updates"

### **What Happens**

- Automatically scans dependencies
- Creates PR for updates
- Includes security fixes
- You approve and merge

---

## 🛡️ **Security Features**

### **Code Scanning**

Automatically scan code for vulnerabilities:

1. Go to Settings
2. Click "Code security"
3. Enable CodeQL analysis

Creates file: `.github/workflows/codeql.yml`

### **Secret Scanning**

Prevents accidentally pushing credentials:
1. Automatically scans commits
2. Alerts if secrets found
3. Revoke keys immediately

### **Branch Protection**

Protect main branch from mistakes:

1. Go to Settings
2. Click "Branches"
3. Click "Add rule"
4. Branch name pattern: `main`
5. Enable:
   - Require pull request reviews (2+)
   - Require status checks to pass
   - Require branches to be up to date
   - Include administrators

---

## 👥 **Teams & Organizations**

### **Creating an Organization**

1. Click profile icon
2. Click "Settings"
3. Click "Organizations"
4. Click "New organization"
5. Choose plan, add name
6. Add members

### **Organization Benefits**

- Centralized repository management
- Team-based permissions
- Audit logs
- Single billing
- Organization-wide settings

### **Teams within Organizations**

Create teams for different groups:
- **Backend Team** - Manage backend repos
- **DevOps Team** - Manage infrastructure
- **Marketing Team** - Manage docs/website

Set different permissions for each team.

---

## 📝 **GitHub Pages (Free Website)**

**GitHub Pages** hosts static websites for free.

### **Creating a Site**

1. Create repository: `username.github.io`
2. Add HTML files
3. Push to GitHub
4. Site available at: `https://username.github.io`

### **Jekyll (Static Site Generator)**

```yaml
# _config.yml
title: My Blog
theme: jekyll-theme-minimal
```

**Homepage:**
```markdown
---
layout: default
title: Welcome
---

# My Blog

Posts about development...
```

---

## 🚀 **GitHub Sponsors**

Allow users to support your work:

1. Go to profile
2. Click "Sponsor"
3. Set up sponsorship page
4. Choose funding options
5. Share with community

---

## 📱 **GitHub App & Desktop**

### **GitHub Desktop** (Visual Git)

Alternative to command line:
1. Download from github.com/desktop
2. Sign in with GitHub
3. Clone repositories visually
4. Commit, push, pull graphically
5. No terminal needed

### **GitHub Mobile App**

Stay updated on the go:
- View repositories
- Review pull requests
- Respond to issues
- Manage notifications
- Browse code

---

## ✨ **Next Steps**

Learn about: **07-Best-Practices.md**

You'll learn professional workflows and team collaboration strategies!
