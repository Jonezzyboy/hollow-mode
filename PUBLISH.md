# Publishing the Hollow Mode Plugin

## Quick Start

Your plugin is ready to publish! Here's the complete directory structure:

```
hollow-mode-plugin/
├── .claude-plugin/
│   └── plugin.json           # Plugin manifest
├── skills/
│   └── hollow-mode/
│       └── SKILL.md          # The hollow-mode skill
├── README.md                 # Documentation
├── LICENSE                   # MIT License
├── .gitignore               # Git ignore rules
└── PUBLISH.md               # This file
```

## Option 1: Publish to GitHub (Recommended)

### Step 1: Initialize Git Repository

```bash
cd ~/code/jonezzyboy/hollow-mode-plugin
git init
git add .
git commit -m "Initial commit: Hollow Mode plugin v1.0.0"
```

### Step 2: Create GitHub Repository

1. Go to https://github.com/new
2. Name: `hollow-mode` (or `claude-hollow-mode`)
3. Description: "TDD scaffolding with empty implementations for learning"
4. Public repository (so others can install it)
5. Don't initialize with README (you already have one)

### Step 3: Push to GitHub

```bash
git remote add origin https://github.com/YOUR-USERNAME/hollow-mode.git
git branch -M main
git push -u origin main
```

### Step 4: Create a Release (Optional but Recommended)

```bash
# Tag the release
git tag -a v1.0.0 -m "Release v1.0.0: Initial hollow-mode plugin"
git push origin v1.0.0
```

On GitHub:
1. Go to "Releases" → "Create a new release"
2. Choose tag: v1.0.0
3. Title: "v1.0.0 - Initial Release"
4. Description: Copy from README.md highlights
5. Publish release

### Step 5: Users Can Install

Users can now install with:
```bash
claude plugin install hollow-mode@github:YOUR-USERNAME/hollow-mode
```

Or if you tagged a release:
```bash
claude plugin install hollow-mode@github:YOUR-USERNAME/hollow-mode@v1.0.0
```

## Option 2: Create a Plugin Marketplace

If you want to create a discoverable marketplace:

### Create marketplace.json

```json
{
  "name": "jonezzyboy's Claude Plugins",
  "description": "Learning-focused plugins for Claude Code",
  "owner": {
    "name": "Alan Jones",
    "url": "https://github.com/YOUR-USERNAME"
  },
  "plugins": [
    {
      "name": "hollow-mode",
      "description": "TDD scaffolding with empty implementations for learning",
      "source": "github:YOUR-USERNAME/hollow-mode",
      "version": "1.0.0"
    }
  ]
}
```

Host this on GitHub (e.g., in a `claude-marketplace` repository).

Users add your marketplace:
```bash
claude plugin add-marketplace https://raw.githubusercontent.com/YOUR-USERNAME/claude-marketplace/main/marketplace.json
```

Then install:
```bash
claude plugin install hollow-mode
```

## Option 3: Contribute to Official Plugin Registry

Consider submitting to Anthropic's official plugin registry (if available):
1. Fork the official registry repository
2. Add your plugin to the registry
3. Submit a pull request

Check https://github.com/anthropics/claude-code for contribution guidelines.

## Testing Before Publishing

### Test Locally

Before publishing, test the plugin locally:

```bash
# From any project directory
claude --plugin-dir ~/code/jonezzyboy/hollow-mode-plugin

# Then in Claude Code, try:
# "Use hollow-mode to help me create a TDD exercise for X"
```

Verify:
- ✅ Skill appears in `/help` as `/hollow-mode:hollow-mode`
- ✅ Asks design questions before creating files
- ✅ Creates empty stubs (no implementation)
- ✅ Refuses to implement when asked
- ✅ Provides helpful coaching without code

## Updating the Plugin

### Increment Version

Edit `.claude-plugin/plugin.json`:
```json
{
  "version": "1.1.0"  // Follow semantic versioning
}
```

### Version Guidelines (Semantic Versioning)

- **PATCH** (1.0.X): Bug fixes, typo corrections
- **MINOR** (1.X.0): New features, improvements (backward compatible)
- **MAJOR** (X.0.0): Breaking changes

### Publish Update

```bash
git add .
git commit -m "Release v1.1.0: [describe changes]"
git tag -a v1.1.0 -m "Release v1.1.0"
git push origin main --tags
```

Users update with:
```bash
claude plugin update hollow-mode
```

## Sharing with the Community

### Where to Share

1. **Claude Code GitHub Discussions**
   - https://github.com/anthropics/claude-code/discussions

2. **Reddit**
   - r/ClaudeAI
   - r/programming (if it gets traction)

3. **Twitter/X**
   - Tag @AnthropicAI
   - Use #ClaudeCode hashtag

4. **Dev.to or Hashnode**
   - Write a blog post about the methodology
   - "How Hollow Mode Teaches TDD Better Than Tutorials"

### Example Announcement Post

```markdown
# Introducing Hollow Mode: Learn TDD by Doing, Not Reading

I've created a Claude Code plugin that helps you learn programming through
active implementation instead of passive consumption.

**What it does:**
- Creates comprehensive TDD test suites
- Generates empty function stubs
- Refuses to implement code (even when you beg!)
- Provides coaching through pseudocode and discussion

**Why it works:**
Reading code: ~10% retention
Implementing from tests: ~70% retention

Install: `claude plugin install hollow-mode@github:YOUR-USERNAME/hollow-mode`

Created using TDD methodology - tested with real pressure scenarios!
```

## Support & Maintenance

### Enable GitHub Issues

Users can report:
- Bugs (hollow mode broken, implementation leaked)
- Feature requests (new learning modes)
- Questions (how to use effectively)

### Monitor Usage

Watch for:
- Stars (gauge interest)
- Issues (user pain points)
- Forks (community adoption)

## Analytics (Optional)

Consider adding:
- Download statistics (via GitHub API)
- Usage examples from community
- Success stories from learners

## License Note

Your plugin uses MIT License - very permissive:
- ✅ Commercial use allowed
- ✅ Modifications allowed
- ✅ Distribution allowed
- ✅ Private use allowed
- ❌ No warranty
- ❌ No liability

## Next Steps

1. [ ] Update `plugin.json` with your real GitHub URL
2. [ ] Update `README.md` with your real GitHub username
3. [ ] Initialize Git repository
4. [ ] Create GitHub repository
5. [ ] Push to GitHub
6. [ ] Test installation from GitHub
7. [ ] Create v1.0.0 release
8. [ ] Share with community
9. [ ] Iterate based on feedback

## Need Help?

- Claude Code docs: https://github.com/anthropics/claude-code
- Plugin system: Check `/help plugins` in Claude Code
- Community: GitHub Discussions

---

Good luck! You've built something that can genuinely help people learn programming more effectively! 🚀
