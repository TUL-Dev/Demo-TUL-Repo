# Exercise 2: Working with Branches

Learn how to create, switch, and manage branches in Git.

## Objective
Understand how branches work and why they're essential for collaborative development.

## What are Branches?
Branches allow you to work on new features or fixes without affecting the main codebase. Think of them as parallel universes where you can experiment safely!

## Steps

### 1. View Existing Branches
```bash
git branch
```

The branch with an asterisk (*) is your current branch.

To see all branches (including remote):
```bash
git branch -a
```

### 2. Create a New Branch
```bash
git branch feature/my-new-feature
```

**Naming conventions:**
- `feature/` - for new features
- `fix/` - for bug fixes
- `docs/` - for documentation
- `test/` - for testing

### 3. Switch to Your New Branch
```bash
git checkout feature/my-new-feature
```

Or create and switch in one command:
```bash
git checkout -b feature/my-new-feature
```

### 4. Make Changes in Your Branch
```bash
echo "This is a new feature!" > practice-files/new-feature.txt
git add practice-files/new-feature.txt
git commit -m "Add new feature file"
```

### 5. Push Your Branch to Remote
```bash
git push origin feature/my-new-feature
```

Or set upstream and push:
```bash
git push -u origin feature/my-new-feature
```

### 6. Switch Back to Main Branch
```bash
git checkout main
```

Notice that your new feature file isn't there! It only exists in your feature branch.

### 7. List All Your Branches
```bash
git branch -a
```

## Challenge

1. Create a branch called `feature/your-name`
2. Add a file with your favorite programming quote
3. Commit your changes
4. Push the branch to remote
5. Switch back to main
6. Verify your file doesn't appear in main

## Branch Visualization

```
main       A---B---C
                    \
feature             D---E
```

Main branch continues with commits A, B, C while your feature branch diverges at C and has commits D, E.

## Common Commands

| Command | Description |
|---------|-------------|
| `git branch` | List local branches |
| `git branch <name>` | Create a new branch |
| `git checkout <name>` | Switch to a branch |
| `git checkout -b <name>` | Create and switch to new branch |
| `git branch -d <name>` | Delete a branch (safe) |
| `git branch -D <name>` | Force delete a branch |
| `git push origin <name>` | Push branch to remote |

## Best Practices

1. Always create a new branch for new work
2. Use descriptive branch names
3. Keep branches focused on one feature/fix
4. Regularly commit your work
5. Keep your branch updated with main

## Common Issues

**Issue:** "Branch already exists"
**Solution:** Choose a different name or delete the old branch first

**Issue:** "Cannot delete branch - not fully merged"
**Solution:** Make sure to merge or use `-D` to force delete

## Key Takeaways

- Branches allow parallel development
- Always work in feature branches, not main
- Use clear naming conventions
- Push branches to share with others

## Next Steps
Move on to [Exercise 3: Merging Branches](../intermediate/01-merging.md)
