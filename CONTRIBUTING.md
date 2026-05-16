# Contributing to Conn

Thank you for your interest in contributing to Conn! We welcome contributions from everyone, especially GSSoC 2026 participants.

## 🚀 Getting Started

### For GSSoC 2026 Participants

1. **Follow Up**
2. **Fork the repository** on GitHub
3. **Star the repository** (optional but appreciated!)
4. **Clone your fork** locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/Conn.git
   cd Conn
   ```
4. **Add the original repository as upstream**:
   ```bash
   git remote add upstream https://github.com/mayo-byte07/Conn.git
   ```

## 🛠️ Development Setup

For detailed installation and setup instructions, please refer to the [README.md](README.md#quick-start-local-development) Quick Start section.

**Quick reference:**
- Fork and clone the repository
- Run `npm install`
- Set up your `.env` file with Supabase credentials
- Run `npm start` to begin development

## 📋 GSSoC 2026 Guidelines

### Issue Selection

- Look for issues labeled `gssoc`, `good first issue`, or `help wanted`
- Comment on the issue with "I would like to work on this" before starting
- Wait for maintainer assignment before beginning work
- One issue per contributor at a time (unless approved otherwise)

### Branch Naming

Use descriptive branch names:
- `gssoc/feature/your-feature-name`
- `gssoc/fix/issue-description`
- `gssoc/docs/update-documentation`

### Commit Messages

Follow conventional commit format:
- `feat: add dark mode toggle`
- `fix: resolve login authentication error`
- `docs: update API documentation`
- `style: format code with prettier`
- `refactor: simplify link management logic`
- `test: add unit tests for auth module`

### Pull Request Process

1. **Update your branch** with the latest changes from upstream:
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

2. **Commit your changes** with clear messages

3. **Push to your fork**:
   ```bash
   git push origin gssoc/feature/your-feature-name
   ```

4. **Create a Pull Request** with:
   - Clear title describing the change
   - Detailed description of what you did and why
   - Reference the related issue number (e.g., "Fixes #123")
   - Screenshots for UI changes
   - Link to deployed preview (if applicable)

5. **PR Title Format for GSSoC**:
   - `[GSSoC] Add feature: description`
   - `[GSSoC] Fix issue: description`

## 🎯 Code Style Guidelines

### JavaScript
- Use camelCase for variables and functions
- Use PascalCase for classes and constructors
- Add JSDoc comments for complex functions
- Keep functions small and focused

### HTML/CSS
- Use semantic HTML elements
- Follow BEM naming convention for CSS classes
- Ensure responsive design (mobile-first approach)
- Test on multiple screen sizes

### General
- Write clean, readable code
- Add comments for complex logic
- Remove console.log statements before submitting
- Ensure no sensitive data is committed

## 🧪 Testing

- Test your changes thoroughly before submitting
- Check for cross-browser compatibility
- Test on mobile devices
- Verify existing features still work

## 📝 Documentation

- Update relevant documentation if your change affects it
- Add comments to complex code sections
- Update API documentation if you modify endpoints
- Add examples for new features

## 🐛 Bug Reports

When reporting bugs, include:
- Clear description of the problem
- Steps to reproduce
- Expected vs actual behavior
- Screenshots if applicable
- Environment details (OS, browser, Node.js version)

## 💡 Feature Requests

When suggesting features:
- Describe the use case
- Explain why it would be valuable
- Consider implementation complexity
- Provide mockups if it's a UI change


## ⭐ GSSoC 2026 Specific Rules

1. **Quality over quantity**: Focus on meaningful contributions
2. **Communication is key**: Keep maintainers updated on your progress
3. **Ask for help**: If you're stuck, reach out via Discussions
4. **Be patient**: Reviewers may take time to respond
5. **Learn and grow**: Use this opportunity to improve your skills

## 📊 Project Areas for Contribution

- **Frontend**: UI improvements, new themes, animations
- **Backend**: API optimizations, new endpoints
- **Database**: Schema improvements, query optimization
- **Features**: Analytics, social integrations, payment flows
- **Documentation**: README, API docs, tutorials
- **Testing**: Unit tests, integration tests
- **Bug Fixes**: Any reported issues

## 🎉 Recognition

- Contributors will be listed in the CONTRIBUTORS.md file
- Outstanding contributions may be featured in project releases
- GSSoC participants who complete their goals will receive certificates

---

**Happy Contributing!** 🚀

For project contact information, please see the [README.md](README.md#contact) Contact section.
