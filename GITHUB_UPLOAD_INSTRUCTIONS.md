# GitHub Upload Instructions

## Step-by-Step Guide to Upload Your MERN Project

---

## Prerequisites
✅ Git installed on your system
✅ GitHub account created
✅ Repository created: https://github.com/sumzbiz/mern-stack-app.git

---

## Step 1: Initialize Git (if not already done)

Open your terminal in the project directory and run:

```bash
# Check if git is already initialized
git status
```

If you see "fatal: not a git repository", initialize it:

```bash
git init
```

---

## Step 2: Configure Git (First Time Only)

If you haven't configured Git before:

```bash
# Set your name
git config --global user.name "Your Name"

# Set your email (use your GitHub email)
git config --global user.email "your-email@example.com"
```

---

## Step 3: Add Remote Repository

```bash
# Add your GitHub repository as remote
git remote add origin https://github.com/sumzbiz/mern-stack-app.git

# Verify remote was added
git remote -v
```

You should see:
```
origin  https://github.com/sumzbiz/mern-stack-app.git (fetch)
origin  https://github.com/sumzbiz/mern-stack-app.git (push)
```

---

## Step 4: Stage Your Files

The `.gitignore` has been updated to exclude:
- `jenkins_ansible_project_ideas.md`
- `AWS_EC2_DEPLOYMENT_GUIDE.md`

Now stage all files:

```bash
# Add all files (respecting .gitignore)
git add .

# Check what will be committed
git status
```

You should see files like:
- ✅ `docker-compose.yaml`
- ✅ `README.md`
- ✅ `mern/backend/`
- ✅ `mern/frontend/`
- ✅ `.gitignore`
- ❌ `jenkins_ansible_project_ideas.md` (excluded)
- ❌ `AWS_EC2_DEPLOYMENT_GUIDE.md` (excluded)

---

## Step 5: Commit Your Changes

```bash
# Commit with a descriptive message
git commit -m "Initial commit: MERN stack with Docker and distroless images"
```

---

## Step 6: Push to GitHub

### Option A: If repository is empty (recommended)

```bash
# Push to main branch
git branch -M main
git push -u origin main
```

### Option B: If repository already has content

```bash
# Pull existing content first
git pull origin main --allow-unrelated-histories

# Then push
git push -u origin main
```

---

## Step 7: Verify Upload

1. Go to https://github.com/sumzbiz/mern-stack-app
2. Refresh the page
3. You should see all your files uploaded

---

## Troubleshooting

### Issue 1: Authentication Failed

**For HTTPS (recommended):**

GitHub no longer accepts passwords. Use a Personal Access Token (PAT):

1. Go to GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
2. Click "Generate new token (classic)"
3. Give it a name: "MERN Stack App"
4. Select scopes: `repo` (full control)
5. Click "Generate token"
6. **COPY THE TOKEN** (you won't see it again!)

When pushing, use:
- Username: your GitHub username
- Password: paste the token

**Or use SSH (alternative):**

```bash
# Change remote to SSH
git remote set-url origin git@github.com:sumzbiz/mern-stack-app.git

# Generate SSH key (if you don't have one)
ssh-keygen -t ed25519 -C "your-email@example.com"

# Copy public key
cat ~/.ssh/id_ed25519.pub

# Add to GitHub: Settings → SSH and GPG keys → New SSH key
```

---

### Issue 2: Remote Already Exists

```bash
# Remove existing remote
git remote remove origin

# Add it again
git remote add origin https://github.com/sumzbiz/mern-stack-app.git
```

---

### Issue 3: Files Still Being Tracked

If the excluded files were previously committed:

```bash
# Remove from Git tracking (but keep local file)
git rm --cached jenkins_ansible_project_ideas.md
git rm --cached AWS_EC2_DEPLOYMENT_GUIDE.md

# Commit the removal
git commit -m "Remove documentation files from tracking"

# Push
git push origin main
```

---

### Issue 4: Merge Conflicts

If you get merge conflicts when pulling:

```bash
# Option 1: Force push (if you're sure local is correct)
git push -f origin main

# Option 2: Merge manually
git pull origin main
# Resolve conflicts in files
git add .
git commit -m "Resolve merge conflicts"
git push origin main
```

---

## Future Updates

After initial upload, to push new changes:

```bash
# Stage changes
git add .

# Commit
git commit -m "Your commit message"

# Push
git push origin main
```

---

## Useful Git Commands

```bash
# Check status
git status

# View commit history
git log --oneline

# View remote URL
git remote -v

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Discard all local changes
git reset --hard HEAD

# Create a new branch
git checkout -b feature-name

# Switch branches
git checkout main

# View differences
git diff
```

---

## Quick Command Summary

```bash
# One-time setup
git init
git remote add origin https://github.com/sumzbiz/mern-stack-app.git

# Upload to GitHub
git add .
git commit -m "Initial commit: MERN stack with Docker"
git branch -M main
git push -u origin main

# Future updates
git add .
git commit -m "Update message"
git push origin main
```

---

**🎉 Your project is now on GitHub!**
