# Exercise 1: Basic Git Workflow

Learn the fundamental Git commands for tracking and saving your work.

## Objective
Master the basic Git workflow: clone, add, commit, and push.

## Prerequisites
- Git installed on your computer
- A GitHub account
- This repository cloned locally

## Steps

### 1. Check Repository Status
First, let's see the current state of your repository:

```bash
git status
```

This shows which files are modified, staged, or untracked.

### 2. Create Your First File
Create a new file in the `practice-files/` directory:

```bash
cd practice-files
echo "My name is [Your Name] and I'm learning Git!" > my-first-file.txt
```

### 3. Check Status Again
```bash
git status
```

You should see your new file listed as "untracked".

### 4. Stage Your File
Add your file to the staging area:

```bash
git add my-first-file.txt
```

Or stage all changes:

```bash
git add .
```

### 5. Commit Your Changes
Save your changes with a descriptive message:

```bash
git commit -m "Add my first practice file"
```

**Tip:** Good commit messages are:
- Clear and descriptive
- Written in present tense
- Explain what and why (not how)

### 6. Push to Remote
Upload your changes to GitHub:

```bash
git push origin main
```

### 7. View Your Commit History
```bash
git log
```

Or for a compact view:

```bash
git log --oneline
```

## Challenge

1. Create three more files with different content
2. Stage and commit them in separate commits
3. Push all commits to the remote repository
4. Use `git log` to see your commit history

## Common Issues

**Issue:** "Permission denied" when pushing
**Solution:** Make sure you have write access to the repository and your credentials are set up correctly.

**Issue:** "Your branch is behind"
**Solution:** Pull the latest changes first: `git pull origin main`

## Key Takeaways

- `git status` - Check what's changed
- `git add` - Stage files for commit
- `git commit -m "message"` - Save your changes
- `git push` - Upload to remote repository
- `git log` - View commit history

## Next Steps
Move on to [Exercise 2: Working with Branches](../beginner/02-branches.md)
