# Exercise 3: Merging Branches

Learn how to combine changes from different branches.

## Objective
Master the art of merging branches and understand different merge strategies.

## What is Merging?
Merging is the process of integrating changes from one branch into another. It's how you incorporate your feature work back into the main codebase.

## Steps

### 1. Ensure You're on the Target Branch
First, switch to the branch you want to merge INTO (usually main):

```bash
git checkout main
```

### 2. Update Your Local Main Branch
Always pull the latest changes before merging:

```bash
git pull origin main
```

### 3. Merge Your Feature Branch
```bash
git merge feature/my-new-feature
```

If there are no conflicts, Git will automatically create a merge commit.

### 4. Push the Merged Changes
```bash
git push origin main
```

### 5. Delete the Feature Branch (Optional)
After successful merge, you can delete the feature branch:

```bash
# Delete local branch
git branch -d feature/my-new-feature

# Delete remote branch
git push origin --delete feature/my-new-feature
```

## Merge Strategies

### Fast-Forward Merge
When there are no new commits on main since you branched off:

```
Before:
main        A---B
                 \
feature          C---D

After:
main        A---B---C---D
```

### Three-Way Merge
When both branches have new commits:

```
Before:
main        A---B---C
                 \
feature          D---E

After:
main        A---B---C---M
                 \       /
feature          D---E--
```

## Practice Exercise

### Part 1: Simple Merge
1. Create a branch called `feature/greeting`
2. Add a file `greeting.txt` with "Hello World!"
3. Commit and push your branch
4. Switch to main and merge your feature branch

```bash
git checkout -b feature/greeting
echo "Hello World!" > practice-files/greeting.txt
git add practice-files/greeting.txt
git commit -m "Add greeting file"
git push origin feature/greeting

git checkout main
git merge feature/greeting
git push origin main
```

### Part 2: Merge with New Commits
1. Create branch `feature/add-numbers`
2. Add a file with some numbers
3. BEFORE merging, switch to main and make a different change
4. Now merge your feature branch

```bash
git checkout -b feature/add-numbers
echo "1, 2, 3, 4, 5" > practice-files/numbers.txt
git add practice-files/numbers.txt
git commit -m "Add numbers file"

git checkout main
echo "Main branch update" > practice-files/main-update.txt
git add practice-files/main-update.txt
git commit -m "Update main branch"

git merge feature/add-numbers
git push origin main
```

## Understanding Merge Commits

A merge commit has TWO parent commits:
- One from your current branch (main)
- One from the branch being merged (feature)

View merge commits:
```bash
git log --graph --oneline --all
```

## Common Commands

| Command | Description |
|---------|-------------|
| `git merge <branch>` | Merge specified branch into current branch |
| `git merge --no-ff <branch>` | Force create merge commit (no fast-forward) |
| `git merge --abort` | Cancel a merge in progress |
| `git log --graph` | View branch history visually |

## Best Practices

1. **Always pull before merging** - Ensure main is up to date
2. **Merge from main into feature** - Keep your feature branch updated
3. **Test before merging** - Make sure your code works
4. **Use descriptive merge messages** - Explain what's being integrated
5. **Delete merged branches** - Keep your branch list clean

## Common Issues

**Issue:** "Already up to date"
**Solution:** Your branch has no new changes to merge

**Issue:** "Automatic merge failed"
**Solution:** You have merge conflicts - see next exercise!

## Key Takeaways

- Merging combines changes from different branches
- Fast-forward merges are simple and clean
- Three-way merges create merge commits
- Always update main before merging
- Clean up branches after merging

## Next Steps
Move on to [Exercise 4: Handling Merge Conflicts](../intermediate/02-merge-conflicts.md)
