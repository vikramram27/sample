# Sample App - Automated Release Demo

This repository demonstrates automated release workflows using GitHub Actions with tag-based releases.

## 🚀 Release Workflow

### How It Works

This project uses GitHub Actions to automatically create releases when you push a version tag.

#### **Tag-Based Releases**
When you create and push a version tag (v*.*.*), a release is automatically created with categorized changelog.

```bash
# Create a new version tag
git tag v1.0.0

# Push the tag to trigger release
git push origin v1.0.0
```

**What happens:**
- GitHub Action detects the tag push
- Automatically generates a categorized changelog based on PR labels
- Creates a **production release** with the tag name
- Release notes are organized by categories (Breaking Changes, Features, Fixes, etc.)

## 📋 Workflow Features

- ✅ **Auto-labeling from AI commit messages** - Works with GitHub AI/Copilot commits
- ✅ Automatic categorized changelog generation
- ✅ Conventional commits support (feat:, fix:, breaking:, etc.)
- ✅ PR label-based organization
- ✅ Semantic versioning support (v1.0.0, v2.1.3, etc.)
- ✅ Excludes documentation and ignored PRs
- ✅ Custom changelog categories with emojis
- ✅ Full git history for comparison

## 🤖 GitHub AI Commit Integration

This workflow **automatically works with GitHub AI-generated commit messages**! 

When you use the AI sparkle ✨ button in VS Code to generate commits like:
- `feat: Add new feature` → Auto-labeled as `feature`
- `fix: Bug fix` → Auto-labeled as `fix`  
- `breaking:` or `feat!:` → Auto-labeled as `breaking`

**No manual labeling needed!** See [GITHUB_AI_COMMITS.md](GITHUB_AI_COMMITS.md) for full details.

## 🏷️ PR Labels for Changelog

Use these labels on your Pull Requests to organize the changelog:

### Categories
- `breaking` → **Breaking Changes 🛠**
- `feature` → **New Features 🎉**
- `fix` → **Fixes 🔧**
- No label or other labels → **Other Changes**

### Excluded from Changelog
- `ignore-for-release` - Completely excluded
- `documentation` - Excluded from release notes

## 🛠️ Setup Instructions

1. **Clone the repository:**
   ```bash
   git clone git@github.com:vikramram27/sample.git
   cd sample
   ```

2. **Create a feature branch and make changes:**
   ```bash
   # Create a branch
   git checkout -b feature/my-feature
   
   # Edit files
   vim app.js
   
   # Commit changes
   git add .
   git commit -m "feat: Add new feature"
   git push origin feature/my-feature
   ```

3. **Create a Pull Request on GitHub:**
   - Add appropriate labels: `feature`, `fix`, `breaking`, etc.
   - Merge the PR to main

4. **Create a release tag:**
   ```bash
   git checkout main
   git pull
   git tag v1.0.0
   git push origin v1.0.0
   ```
   
   The workflow will automatically create a release with categorized notes!

## 🏷️ Version Tagging Convention

Follow semantic versioning:
- `v1.0.0` - Major release (breaking changes)
- `v1.1.0` - Minor release (new features)
- `v1.1.1` - Patch release (bug fixes)

## 📦 What's Included

- **GitHub Actions Workflow** (`.github/workflows/release.yml`)
  - Triggered by tags and main branch pushes
  - Automatic changelog generation
  - Release creation with notes
itoring Releial releases
2. Main branch pushes create drafts for review
3. Edit draft releases before publishing if needed
4. Delete unwanted tags: `git tag -d v1.0.0 && git push origin :refs/tags/v1.0.0`

## 📝 Example Workflow

```bash
# 1. Create feature branch
git checkout -b feature/awesome-feature

# 2. Make changes
echo "console.log('New feature!');" >> app.js

# 3. Commit and push
git add .
git commit -m "feat: Add awesome feature"
git push origin feature/awesome-feature

# 4. Create PR on GitHub with label "feature"
# 5. Merge PR to main

# 6. Create release tag
git checkout main
git pull
git tag v1.1.0
git push origin v1.1.0

# ✨ Production release v1.1.0 is now live with categorized changelog!
```

## 🔒 Required Permissions

The workflow requires `contents: write` permission to create releases. This is configured in the workflow file.

## License

MIT
