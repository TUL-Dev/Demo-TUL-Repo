# Exercise 5: Pull Requests and Code Review

Learn how to create pull requests and participate in code reviews.

## Objective
Master the collaborative workflow using pull requests for code review and integration.

## What is a Pull Request?

A pull request (PR) is a way to propose changes to a repository. It allows:
- Code review before merging
- Discussion about the changes
- Automated testing
- Collaborative improvement

## Creating a Pull Request

### Method 1: Using GitHub Web Interface

1. Push your branch to GitHub:
```bash
git push origin feature/my-feature
```

2. Go to the repository on GitHub
3. Click "Compare & pull request" button
4. Fill in the PR template:
   - Clear title
   - Description of changes
   - Reference any related issues
5. Click "Create pull request"

### Method 2: Using GitHub CLI

```bash
# Install gh CLI first: https://cli.github.com/

# Create PR from command line
gh pr create --title "Add new feature" --body "Description of changes"

# Create with options
gh pr create --title "Fix bug" --body "Details..." --assignee @me --label bug
```

## Pull Request Template

Create a `.github/pull_request_template.md` file for consistency:

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Refactoring

## Testing
How has this been tested?

## Checklist
- [ ] My code follows the project's style guidelines
- [ ] I have tested my changes
- [ ] I have commented my code where needed
- [ ] I have updated the documentation
```

## Code Review Best Practices

### As a Reviewer

1. **Be constructive and kind**
   - Good: "Consider using a Set here for O(1) lookup performance"
   - Avoid: "This is wrong, use a Set"

2. **Focus on the code, not the person**
   - Good: "This function could be simplified"
   - Avoid: "You wrote this function badly"

3. **Ask questions**
   - "Why did you choose this approach?"
   - "Have you considered...?"

4. **Acknowledge good work**
   - "Nice solution!"
   - "Great use of that pattern"

5. **Check for:**
   - Code correctness
   - Security issues
   - Performance concerns
   - Test coverage
   - Documentation
   - Style consistency

### As a PR Author

1. **Write a clear description**
   - What changes are made?
   - Why are they needed?
   - How do they work?

2. **Keep PRs small and focused**
   - One feature or fix per PR
   - Easier to review
   - Faster to merge

3. **Respond to feedback professionally**
   - Thank reviewers
   - Ask for clarification if needed
   - Make requested changes or explain why not

4. **Keep your PR updated**
   - Merge main into your branch regularly
   - Resolve conflicts promptly

## Practice Exercise

### Exercise 1: Create Your First PR

1. Create a branch with your name
2. Add your favorite coding resource to a shared file
3. Push the branch
4. Create a pull request
5. Wait for review or self-merge for practice

```bash
git checkout -b add-my-resource
echo "- [Resource Name](url) - Description" >> resources.md
git add resources.md
git commit -m "Add my favorite coding resource"
git push origin add-my-resource

# Create PR via GitHub or:
gh pr create --title "Add my favorite coding resource" --body "Added a helpful resource I use for learning"
```

### Exercise 2: Review Someone Else's PR

1. Find an open PR in the repository
2. Read through the changes
3. Leave at least one constructive comment
4. Approve if it looks good, or request changes

```bash
# List open PRs
gh pr list

# Check out a PR locally
gh pr checkout 123

# Test the changes
# Then comment via GitHub UI or:
gh pr review 123 --comment --body "Looks good!"
```

### Exercise 3: Handle Review Feedback

1. Create a PR with intentional issues
2. Have a peer review it
3. Address the feedback
4. Push updates to the same branch
5. Get approval and merge

## PR Workflow Commands

```bash
# Create a new branch for your PR
git checkout -b feature/new-feature

# Make changes and commit
git add .
git commit -m "Implement new feature"

# Push to remote
git push origin feature/new-feature

# Create PR (using gh CLI)
gh pr create

# Update PR with new commits
git commit -m "Address review feedback"
git push origin feature/new-feature

# Merge PR (after approval)
gh pr merge 123

# Or via Git commands after GitHub merge
git checkout main
git pull origin main
git branch -d feature/new-feature
```

## Common PR Workflows

### Workflow 1: Feature Branch
```
main ──────o────────o──M
            \          /
feature      o──o──o──
```

### Workflow 2: Fork and PR
1. Fork the repository
2. Clone your fork
3. Create feature branch
4. Push to your fork
5. Create PR to original repo

```bash
# Add upstream remote
git remote add upstream https://github.com/original/repo.git

# Keep your fork updated
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

## GitHub PR Features

### Request Reviewers
Assign specific people to review your PR

### Labels
Tag PRs with labels: bug, enhancement, documentation, etc.

### Milestones
Associate PRs with project milestones

### Draft PRs
Create work-in-progress PRs:
```bash
gh pr create --draft
```

### PR Checks
- Automated tests
- Code quality checks
- Security scans
- CI/CD pipelines

## Merging Strategies

### 1. Merge Commit
Preserves full history with merge commit
```bash
gh pr merge 123 --merge
```

### 2. Squash and Merge
Combines all commits into one
```bash
gh pr merge 123 --squash
```

### 3. Rebase and Merge
Replays commits on top of main
```bash
gh pr merge 123 --rebase
```

## Best Practices

1. **Before creating PR:**
   - Update your branch with main
   - Run all tests
   - Check code style
   - Write good commit messages

2. **PR description should include:**
   - What changed
   - Why it changed
   - How to test it
   - Screenshots (for UI changes)

3. **During review:**
   - Respond promptly
   - Be open to feedback
   - Explain your decisions

4. **After merge:**
   - Delete the feature branch
   - Update local repository
   - Close related issues

## Common Issues

**Issue:** "This branch has conflicts"
**Solution:** Merge main into your branch and resolve conflicts

```bash
git checkout feature-branch
git merge main
# Resolve conflicts
git push origin feature-branch
```

**Issue:** "Some checks haven't passed"
**Solution:** Review failed checks and fix issues

**Issue:** "PR is too large"
**Solution:** Break into smaller PRs

## Key Takeaways

- PRs enable code review before merging
- Keep PRs small and focused
- Write clear descriptions
- Be constructive in reviews
- Respond professionally to feedback
- Merge and clean up after approval

## Challenge

**Team Exercise:**
1. Pair up with another learner
2. Each create a PR to add a feature
3. Review each other's PRs
4. Request at least one change
5. Update based on feedback
6. Approve and merge

## Resources

- [GitHub PR Documentation](https://docs.github.com/en/pull-requests)
- [GitHub CLI Manual](https://cli.github.com/manual/)
- [Code Review Best Practices](https://google.github.io/eng-practices/review/)

## Next Steps
Move on to [Exercise 6: Rebasing and History Rewriting](../advanced/02-rebasing.md)
