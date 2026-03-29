# 02 - Installing & Configuring Git

## 🖥️ **Installing Git on Windows**

### **Option 1: Download Installer (Easiest)**

1. Go to: https://git-scm.com/download/win
2. Click **"Download for Windows"** (auto-detects your system)
3. Open the downloaded file (Git-X.XX.X-64-bit.exe)
4. **Installation Steps:**
   - Click "Next" through prompts
   - Choose installation location (default is fine)
   - Select components (leave defaults checked)
   - Choose default editor (Vim, Notepad++, VS Code, etc.)
   - Choose "Use Git from the Windows Command Prompt"
   - Accept HTTPS library (default is fine)
   - Choose line ending conversion (Windows: "Checkout Windows-style")
   - Click "Install"
5. Restart your computer (optional but recommended)

### **Option 2: Using Windows Package Manager (If you have it)**

```powershell
winget install --id Git.Git -e --source winget
```

### **Option 3: Using Chocolatey**

```powershell
choco install git
```

---

## 🍎 **Installing Git on Mac**

### **Option 1: Homebrew (Recommended)**

```bash
brew install git
```

### **Option 2: Official Installer**

1. Go to: https://git-scm.com/download/mac
2. Download the installer for your Mac version
3. Run installer and follow prompts

---

## 🐧 **Installing Git on Linux**

```bash
# Ubuntu / Debian
sudo apt-get install git

# Fedora / RedHat
sudo yum install git

# Arch
sudo pacman -S git
```

---

## ✅ **Verify Installation**

Open Terminal/Command Prompt and run:

```bash
git --version
```

**Expected output:**
```
git version 2.43.0 (or newer)
```

If you see a version number, Git is installed! ✅

---

## 🔧 **Configure Git (Important!)**

### **Set Your Name**

```bash
git config --global user.name "Your Full Name"
```

### **Set Your Email**

```bash
git config --global user.email "your.email@example.com"
```

**Note:** Use the same email you'll use for your GitHub account!

---

## 📋 **Verify Configuration**

### **Check Your Settings**

```bash
git config --global user.name
git config --global user.email
```

**Expected output:**
```
Your Full Name
your.email@example.com
```

### **View All Settings**

```bash
git config --global --list
```

---

## ⚙️ **Optional: Advanced Configuration**

### **Set Default Editor**

```bash
# VS Code
git config --global core.editor "code --wait"

# Notepad++
git config --global core.editor "'C:\Program Files\Notepad++\notepad++.exe'"

# Vim
git config --global core.editor "vim"
```

### **Set Default Branch Name**

(Modern Git uses 'main' instead of 'master')

```bash
git config --global init.defaultBranch main
```

### **Setup SSH (For GitHub - Optional)**

SSH allows you to push/pull without typing your password every time.

**Step 1: Generate SSH Key**

```bash
ssh-keygen -t ed25519 -C "your.email@example.com"
```

**Step 2: Follow prompts (press Enter for defaults)**

```
Enter file in which to save the key: [Press Enter]
Enter passphrase (empty for no passphrase): [Press Enter]
Enter same passphrase again: [Press Enter]
```

**Step 3: Copy your public key**

```bash
# Windows/PowerShell
Get-Content ~/.ssh/id_ed25519.pub | Set-Clipboard

# Mac/Linux
cat ~/.ssh/id_ed25519.pub | pbcopy
```

**Step 4: Add to GitHub**
1. Go to: https://github.com/settings/keys
2. Click "New SSH key"
3. Paste your key
4. Click "Add SSH key"

**Step 5: Test SSH Connection**

```bash
ssh -T git@github.com
```

**Expected output:**
```
Hi yourusername! You've successfully authenticated, but GitHub does not provide shell access.
```

---

## 🌐 **Create GitHub Account**

1. Go to: https://github.com
2. Click "Sign up"
3. Enter email, password, username
4. Verify email address
5. Done! ✅

**Your GitHub URL will be:** `https://github.com/yourusername`

---

## 🧪 **Test Your Setup**

### **Create Your First Local Repository**

```bash
# Create a folder
mkdir my-first-repo
cd my-first-repo

# Initialize Git
git init

# Create a file
echo "Hello GitHub!" > README.md

# Add file to staging
git add README.md

# Commit
git commit -m "Initial commit"

# Check log
git log
```

**Expected output:**
```
commit abc123def456 (HEAD -> main)
Author: Your Name <your.email@example.com>
Date:   Wed Mar 26 10:30:45 2026 +0000

    Initial commit
```

---

## 🎯 **Common Setup Issues**

### **Problem: "git: command not found"**
**Solution:** Git wasn't installed or not in PATH
- Reinstall Git
- Restart Terminal/Command Prompt
- Verify with `git --version`

### **Problem: "Author identity unknown"**
**Solution:** Run:
```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

### **Problem: SSH key not working**
**Solution:** Follow SSH setup steps above or use HTTPS instead

---

## ✨ **Next Steps**

Now that Git is installed and configured, learn: **03-Basic-Commands.md**

You'll learn all the essential commands to work with Git daily!
