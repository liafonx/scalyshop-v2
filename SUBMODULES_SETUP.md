# Git Submodules Setup Guide

This repository uses Git submodules to reference the three component repositories.

## 📦 What are Git Submodules?

Git submodules allow you to keep a Git repository as a subdirectory of another Git repository. This lets you clone another repository into your project and keep your commits separate.

## 🚀 For Users (Cloning the Project)

### Clone Everything at Once

```bash
# Clone main repository with all submodules
git clone --recursive https://github.com/YOUR_USERNAME/scalyshop-v2.git
```

This will clone the main repository and all three component repositories (backend, frontend, cluster-management).

### Clone Main Repo, Then Get Submodules

```bash
# Clone main repository
git clone https://github.com/YOUR_USERNAME/scalyshop-v2.git
cd scalyshop-v2

# Initialize and fetch all submodules
git submodule update --init --recursive
```

## 🔄 Working with Submodules

### Update All Submodules to Latest

```bash
# Pull latest changes from all submodules
git submodule update --remote --recursive
```

### Update Specific Submodule

```bash
# Update just the backend
cd scalyshop-v2-backend
git pull origin main

# Or from main repo
git submodule update --remote scalyshop-v2-backend
```

### Check Submodule Status

```bash
# See which commits submodules are on
git submodule status

# See if there are changes in submodules
git status
```

### Make Changes in a Submodule

```bash
# Navigate to the submodule
cd scalyshop-v2-backend

# Work normally (it's a regular Git repo)
git checkout -b my-feature
# ... make changes ...
git add .
git commit -m "Add new feature"
git push origin my-feature

# Go back to main repo
cd ..

# Main repo tracks which commit the submodule is on
git add scalyshop-v2-backend
git commit -m "Update backend submodule"
git push
```

## 🛠️ For Maintainers (Setting Up Submodules)

### Add Submodules (Already Done)

This project already has submodules configured. For reference, they were added with:

```bash
# Add backend submodule
git submodule add https://github.com/YOUR_USERNAME/scalyshop-v2-backend.git scalyshop-v2-backend

# Add frontend submodule
git submodule add https://github.com/YOUR_USERNAME/scalyshop-v2-frontend.git scalyshop-v2-frontend

# Add cluster management submodule
git submodule add https://github.com/YOUR_USERNAME/scalyshop-cluster-management.git scalyshop-cluster-management

# Commit the .gitmodules file
git commit -m "Add submodules for backend, frontend, and cluster management"
```

### Remove a Submodule

```bash
# Remove submodule from .gitmodules
git submodule deinit -f scalyshop-v2-backend

# Remove from .git/modules
rm -rf .git/modules/scalyshop-v2-backend

# Remove directory
git rm -f scalyshop-v2-backend

# Commit
git commit -m "Remove backend submodule"
```

## 📝 Important Notes

### Submodule Best Practices

1. **Always commit submodule changes first**, then commit the main repo
2. **Communicate with team** when updating submodules
3. **Use specific commits** rather than tracking branches (more stable)
4. **Document dependencies** between submodules if any exist

### Common Pitfalls

❌ **Don't forget `--recursive`** when cloning  
❌ **Don't commit without updating submodules** first  
❌ **Don't modify submodules directly** without proper Git workflow  

✅ **Do use `--recursive`** for all submodule operations  
✅ **Do commit in submodule first**, then main repo  
✅ **Do communicate** submodule updates to team  

## 🔗 Viewing Submodules on GitHub

When you push to GitHub, the submodules will appear as:
- **Folders with @ symbol** and commit hash
- **Clickable links** that go to the specific commit in the submodule repo
- **Visual indication** that it's a submodule, not a regular folder

Example:
```
scalyshop-v2-backend @ a1b2c3d   → Click to view at that specific commit
```

## 📖 Additional Resources

- [Git Submodules Documentation](https://git-scm.com/book/en/v2/Git-Tools-Submodules)
- [GitHub Submodules Guide](https://github.blog/2016-02-01-working-with-submodules/)
- [Atlassian Submodules Tutorial](https://www.atlassian.com/git/tutorials/git-submodule)

## 🆘 Troubleshooting

### "fatal: No url found for submodule"
```bash
# Re-initialize submodules
git submodule update --init --recursive
```

### Submodule folder is empty
```bash
# Fetch submodule content
git submodule update --init --recursive
```

### Submodule shows modified but you didn't change anything
```bash
# Reset to tracked commit
git submodule update --recursive
```

### Want to work on specific branch in submodule
```bash
cd scalyshop-v2-backend
git checkout dev
git pull origin dev
cd ..
git add scalyshop-v2-backend
git commit -m "Update backend to dev branch"
```

