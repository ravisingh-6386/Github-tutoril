# GitHub Quick Reference Cards

## 🗂️ **File Index**

This folder contains everything you need to master GitHub:

1. **00-START-HERE.md** - Overview and learning path
2. **01-What-is-GitHub.md** - Concepts and fundamentals
3. **02-Installing-Git.md** - Setup and configuration
4. **03-Basic-Commands.md** - Essential Git commands
5. **04-Branches-Workflow.md** - Branching strategies
6. **05-Collaboration.md** - PRs, Issues, Forks
7. **06-Advanced-Features.md** - Actions, Projects, Releases
8. **07-Best-Practices.md** - Professional workflows
9. **08-Git-Cheat-Sheet.md** - Quick command reference
10. **09-Examples-Explained.md** - Real-world walkthroughs
11. **10-Common-Issues.md** - Troubleshooting guide

---

## 📋 **Sample .gitignore Files**

### **Python Project**

```
# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
wheels/
*.egg-info/
.installed.cfg
*.egg

# Virtual environments
venv/
ENV/
env/

# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db
```

### **JavaScript/Node Project**

```
# Dependencies
node_modules/
package-lock.json
yarn.lock

# Build
dist/
build/
.next/
out/

# Environment
.env
.env.local
.env.*.local

# IDE
.vscode/
.idea/
*.swp

# OS
.DS_Store
Thumbs.db

# Testing
coverage/
.nyc_output/
```

### **General**

```
# Secrets
.env
secrets.txt
credentials.json
*.pem
*.key

# Logs
logs/
*.log
npm-debug.log*

# Temporary
.tmp/
tmp/
temp/

# OS
.DS_Store
Thumbs.db
.trash/

# IDE
.vscode/
.idea/
*.swp
*.swo
*~
.project
.classpath
```

---

## 📝 **Sample README Template**

```markdown
# Project Name

Brief description of what this project does.

## Features

- Feature one
- Feature two
- Feature three

## Installation

### Prerequisites
- Python 3.9+
- pip

### Steps

\`\`\`bash
# Clone the repo
git clone https://github.com/username/project.git

# Navigate to directory
cd project

# Install dependencies
pip install -r requirements.txt

# Run
python app.py
\`\`\`

## Usage

### Basic Example

\`\`\`python
from project import main
main()
\`\`\`

### Advanced Usage

See [Documentation](./docs) for more.

## Configuration

Create `.env` file:

\`\`\`
DATABASE_URL=postgresql://user:pass@localhost/db
API_KEY=your_api_key_here
\`\`\`

## API Reference

### GET /users

Returns list of users.

\`\`\`
GET /users?page=1&limit=10
\`\`\`

Response:
\`\`\`json
{
  "users": [
    {"id": 1, "name": "John"}
  ]
}
\`\`\`

## Testing

\`\`\`bash
# Run tests
pytest

# With coverage
pytest --cov=src tests/
\`\`\`

## Contributing

1. Fork the repo
2. Create feature branch: \`git checkout -b feature/amazing\`
3. Commit: \`git commit -m "Add amazing feature"\`
4. Push: \`git push origin feature/amazing\`
5. Open Pull Request

## License

MIT License - see LICENSE file for details.

## Contact

- Email: author@example.com
- Twitter: @handle
```

---

## 🏗️ **Sample GitHub Action Workflows**

### **Python Tests**

File: `.github/workflows/tests.yml`

```yaml
name: Tests

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
    
    - name: Lint with flake8
      run: flake8 src/
    
    - name: Test with pytest
      run: pytest tests/ --cov=src/
    
    - name: Upload coverage
      uses: codecov/codecov-action@v3
```

### **Node.js Tests**

File: `.github/workflows/tests.yml`

```yaml
name: Tests

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    
    strategy:
      matrix:
        node-version: [14, 16, 18]
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Use Node.js
      uses: actions/setup-node@v3
      with:
        node-version: ${{ matrix.node-version }}
    
    - name: Install dependencies
      run: npm ci
    
    - name: Lint
      run: npm run lint
    
    - name: Test
      run: npm test
    
    - name: Build
      run: npm run build
```

### **Deploy on Push**

File: `.github/workflows/deploy.yml`

```yaml
name: Deploy

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Deploy to server
      uses: appleboy/ssh-action@master
      with:
        host: ${{ secrets.HOST }}
        username: ${{ secrets.USERNAME }}
        key: ${{ secrets.SSH_KEY }}
        script: |
          cd /var/www/app
          git pull
          npm install
          npm run build
          pm2 restart app
```

---

## 🎯 **Quick Decision Trees**

### **When Should I Create a Branch?**

```
Do I want to:
├─ Add new feature? → YES create branch
├─ Fix a bug? → YES create branch
├─ Make small doc fix? → Maybe (depends on team)
├─ Commit directly to main? → NO! Never!
└─ Test something quickly? → YES create branch (delete later)
```

### **What Type of Commit Message?**

```
What did I do?
├─ Added new feature → "feat: ..."
├─ Fixed a bug → "fix: ..."
├─ Changed docs → "docs: ..."
├─ Improved code → "refactor: ..."
├─ Made tests → "test: ..."
├─ Changed dependency → "chore: ..."
└─ Improved speed → "perf: ..."
```

### **How Do I Undo?**

```
What level of undo?
├─ File changes (before add) → git restore <file>
├─ Staged changes → git restore --staged <file>
├─ Last commit (keep changes) → git reset --soft HEAD~1
├─ Last commit (discard) → git reset --hard HEAD~1
└─ Already pushed → git revert <commit>
```

---

## 🔗 **Useful Resources**

### **Official Docs**
- GitHub Docs: https://docs.github.com
- Git Book: https://git-scm.com/book
- GitHub Skills: https://skills.github.com

### **Learning Platforms**
- GitHub Learning Lab
- Codecademy
- Coursera
- LinkedIn Learning

### **Tools**
- GitHub Desktop - Visual Git client
- GitKraken - Advanced Git GUI
- VS Code - Great Git integration
- GitHub Copilot - AI coding assistance

### **Community**
- Stack Overflow (tag: git, github)
- GitHub Discussions
- Dev.to community
- Reddit (r/git, r/github)

---

## ✨ **You're Ready!**

Congratulations! You now have a comprehensive knowledge of GitHub.

**Remember:**
- Start simple, get comfortable with basics
- Practice regularly
- Don't be afraid to make mistakes (that's how we learn!)
- Help others learn GitHub too

**Happy coding!** 🚀
