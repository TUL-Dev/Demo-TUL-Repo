# Exercise 4: Handling Merge Conflicts

Learn how to resolve conflicts when Git can't automatically merge changes.

## Objective
Understand merge conflicts and learn techniques to resolve them confidently.

## What is a Merge Conflict?
A merge conflict occurs when Git can't automatically determine which changes to keep because the same lines were modified in different branches.

## When Do Conflicts Happen?

Conflicts occur when:
1. Same file, same lines modified in both branches
2. One branch modifies a file while another deletes it
3. Two branches create files with the same name

## Creating a Practice Conflict

Let's intentionally create a conflict to practice resolving it!

### Step 1: Create First Branch
```bash
git checkout main
git checkout -b feature/conflict-branch-1

echo "Version from branch 1" > practice-files/conflict-test.txt
git add practice-files/conflict-test.txt
git commit -m "Add conflict test from branch 1"
```

### Step 2: Create Second Branch (from main)
```bash
git checkout main
git checkout -b feature/conflict-branch-2

echo "Version from branch 2" > practice-files/conflict-test.txt
git add practice-files/conflict-test.txt
git commit -m "Add conflict test from branch 2"
```

### Step 3: Merge First Branch
```bash
git checkout main
git merge feature/conflict-branch-1
# This will succeed
```

### Step 4: Try to Merge Second Branch
```bash
git merge feature/conflict-branch-2
# This will create a CONFLICT!
```

## Understanding Conflict Markers

When a conflict occurs, Git adds markers to the file:

```
<<<<<<< HEAD
Version from branch 1
=======
Version from branch 2
>>>>>>> feature/conflict-branch-2
```

- `<<<<<<< HEAD` - Start of your current branch's version
- `=======` - Separator
- `>>>>>>> branch-name` - End of the incoming branch's version

## Resolving Conflicts

### Method 1: Manual Resolution

1. Open the conflicted file in your editor
2. Look for conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
3. Decide which changes to keep (or keep both!)
4. Remove the conflict markers
5. Stage and commit the resolved file

```bash
# After manually editing the file
git add practice-files/conflict-test.txt
git commit -m "Resolve merge conflict in conflict-test.txt"
```

### Method 2: Choose One Version

Keep the current branch version:
```bash
git checkout --ours practice-files/conflict-test.txt
git add practice-files/conflict-test.txt
```

Keep the incoming branch version:
```bash
git checkout --theirs practice-files/conflict-test.txt
git add practice-files/conflict-test.txt
```

### Method 3: Use a Merge Tool

```bash
git mergetool
```

This opens a visual merge tool (if configured) to help resolve conflicts.

## Practice Exercise

### Exercise 1: Simple Text Conflict

1. Create two branches from main
2. In both branches, modify the same line in a file differently
3. Merge the first branch into main
4. Try to merge the second branch
5. Resolve the conflict manually
6. Complete the merge

### Exercise 2: Multiple Conflicts

1. Create a file with multiple sections
2. Create two branches
3. Modify different parts of the file in each branch
4. Merge and resolve all conflicts

Example file (`team-roster.txt`):
```
Team Members:
- Alice
- Bob
- Charlie

Project: Git Learning
Status: In Progress
```

Branch 1: Add team member and change status
Branch 2: Add different team member and change project name

### Exercise 3: Conflict Resolution Strategies

Practice different resolution approaches:

**Keep both changes:**
```
Version from branch 1
Version from branch 2
```

**Keep one version:**
```
Version from branch 1
```
(or branch 2)

**Create a new solution:**
```
Combined version incorporating both ideas
```

## Checking for Conflicts

Before committing, verify no conflicts remain:

```bash
# Check status
git status

# Search for conflict markers
grep -r "<<<<<<< HEAD" .
```

## Preventing Conflicts

1. **Pull frequently** - Stay updated with main branch
2. **Communicate** - Coordinate who's working on what
3. **Make focused changes** - Smaller, specific changes conflict less
4. **Merge main into feature** - Regularly update your branch

```bash
git checkout feature/my-branch
git merge main
# Resolve any conflicts here, before final merge
```

## Common Commands

| Command | Description |
|---------|-------------|
| `git status` | See which files have conflicts |
| `git diff` | View conflict details |
| `git merge --abort` | Cancel the merge and start over |
| `git checkout --ours <file>` | Keep current branch version |
| `git checkout --theirs <file>` | Keep incoming branch version |
| `git mergetool` | Open visual merge tool |

## Workflow Summary

1. Attempt merge: `git merge feature-branch`
2. Conflict detected! Git pauses the merge
3. Run `git status` to see conflicted files
4. Open and edit conflicted files
5. Remove conflict markers
6. Stage resolved files: `git add <file>`
7. Complete merge: `git commit`

## Common Mistakes

1. **Forgetting to remove conflict markers** - Your code will break!
2. **Not testing after resolution** - Always test the merged code
3. **Committing unresolved conflicts** - Make sure all conflicts are fixed
4. **Panic and `git merge --abort`** - Take your time, conflicts are normal!

## Advanced: Avoiding Conflicts

### Rebase Instead of Merge
```bash
git checkout feature-branch
git rebase main
```

Rebase replays your commits on top of main, which can help avoid some conflicts.

## Key Takeaways

- Conflicts are normal in collaborative development
- Git marks conflicts clearly with `<<<<<<<`, `=======`, `>>>>>>>`
- You have full control over the resolution
- Always test after resolving conflicts
- Communication prevents many conflicts

## Challenge

Work with a partner:
1. Both edit the same file's same lines
2. Both commit to different branches
3. Race to merge first (first one wins!)
4. Second person resolves the conflict
5. Switch roles and repeat

## Next Steps
Move on to [Exercise 5: Pull Requests and Code Review](../advanced/01-pull-requests.md)
