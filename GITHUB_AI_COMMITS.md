# How GitHub AI Commit Messages Work with Release Changelog

## 🤖 GitHub AI Commit Messages

When you use the AI feature in VS Code Git extension, it generates **conventional commits**:

```
feat: Add new user endpoint
fix: Resolve authentication bug
docs: Update API documentation
refactor: Improve code structure
chore: Update dependencies
```

## 🔄 How It Works Together

### Current Setup (Automatic)

1. **You write code** → Use GitHub AI to generate commit message
   ```bash
   # AI generates: "feat: Add new user endpoint"
   git commit -m "feat: Add new user endpoint"
   ```

2. **Create PR** → Our auto-label workflow automatically adds labels
   - `feat:` commits → Adds `feature` label
   - `fix:` commits → Adds `fix` label
   - `breaking:` or `feat!:` → Adds `breaking` label
   - `docs:` commits → Adds `documentation` label

3. **Merge PR** → Labels are already applied ✅

4. **Push tag** → Changelog is automatically categorized!
   ```bash
   git tag v1.2.0
   git push origin v1.2.0
   ```

## 📋 Conventional Commit Mapping

| AI Commit Prefix | Auto Label Added | Changelog Category |
|-----------------|------------------|-------------------|
| `feat:` | `feature` | New Features 🎉 |
| `fix:` | `fix` | Fixes 🔧 |
| `breaking:` or `feat!:` | `breaking` | Breaking Changes 🛠 |
Release Workflow** (`.github/workflows/release.yml`)
- Triggers on version tags
- Generates categorized changelog from PR labels
- Creates GitHub release

✅ **Changelog Config** (`.github/release.yml`)
- Defines categories and labels
- Excludes documentation changes
- Custom emoji categories

## 🎯 Workflow Example

### Step 1: Create Feature Branch
```bash
git checkout -b feature/new-endpoint
# Make changes...
```

### Step 2: Use AI Commit (in VS Code)
1. Stage your changes
2. Click the sparkle ✨ icon in commit message box
3. AI generates: "feat: Add user profile endpoint"
4. Commit and push

### Step 3: Create PR on GitHub
The auto-label workflow automatically adds the `feature` label! 🎉

### Step 4: Merge PR
Your PR is now labeled and ready for release

### Step 5: Create Release
```bash
git checkout main
git pull
git tag v1.2.0
git push origin v1.2.0
```

The release changelog automatically shows:
```
## New Features 🎉
* Add user profile endpoint (#1)
```

## 🔧 Manual Label Override

You can still manually add/remove labels if needed:
- The auto-label runs on every PR update
- Manual labels are preserved
- You have full control

## 💡 Benefits

✅ **Zero manual work** - AI commits → Auto labels → Categorized changelog
✅ **Consistent format** - AI ensures proper conventional commits
✅ **Clean releases** - Professional changelog generation
✅ **Flexible** - Can override labels anytime

## 🚀 Try It Now

The auto-label workflow is already active! Just:
1. Create a branch
2. Use AI commit messages
3. Open a PR
4. Watch labels appear automatically
