# Contributing to Product Planner

Thank you for your interest in contributing to Product Planner! This document provides guidelines and information for contributors.

## 🎯 Ways to Contribute

### 1. Report Bugs 🐛
Found a bug? Please [open an issue](https://github.com/kobe8cong/product-planner/issues/new) with:
- Clear description of the problem
- Steps to reproduce
- Expected vs. actual behavior
- Your environment (OS, Claude Code version)
- Screenshots if applicable

### 2. Suggest Features 💡
Have an idea? We'd love to hear it! [Open a feature request](https://github.com/kobe8cong/product-planner/issues/new) with:
- Problem you're trying to solve
- Proposed solution
- Why it would benefit users
- Any alternatives you've considered

### 3. Improve Documentation 📝
Documentation improvements are always welcome:
- Fix typos or clarify instructions
- Add examples or use cases
- Improve README or guides
- Translate to other languages

### 4. Submit Code 🔧
Code contributions follow our workflow below.

### 5. Share Feedback 💬
Use Product Planner and [share your experience](https://github.com/kobe8cong/product-planner/discussions):
- What worked well?
- What could be better?
- Use cases we didn't consider?

## 🚀 Getting Started

### Prerequisites
- Claude Code CLI or Desktop App installed
- Git for version control
- Text editor (VS Code, Cursor, etc.)
- Basic understanding of Markdown and Claude Code plugins

### Development Setup

1. **Fork and Clone**
   ```bash
   # Fork the repository on GitHub
   git clone https://github.com/YOUR_USERNAME/product-planner.git
   cd product-planner
   ```

2. **Create a Branch**
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/bug-description
   ```

3. **Test Locally**
   ```bash
   # Link to your Claude skills directory
   ln -s $(pwd) ~/.claude/skills/product-planner-dev
   
   # Test in Claude Code
   /product-plan test project
   ```

4. **Make Changes**
   - Edit relevant files
   - Follow code style guidelines (see below)
   - Test your changes thoroughly

5. **Commit**
   ```bash
   git add .
   git commit -m "Brief description of changes"
   ```

6. **Push and Create PR**
   ```bash
   git push origin feature/your-feature-name
   ```
   Then open a Pull Request on GitHub.

## 📋 Pull Request Guidelines

### Before Submitting
- [ ] Changes are tested and work as expected
- [ ] Documentation is updated if needed
- [ ] Commit messages are clear and descriptive
- [ ] Code follows project conventions
- [ ] No breaking changes (or clearly documented)

### PR Description Should Include
- **What**: What does this PR do?
- **Why**: Why is this change needed?
- **How**: How does it work?
- **Testing**: How did you test it?
- **Screenshots**: If UI changes

### Example PR Description
```markdown
## What
Adds export to PDF functionality for PRD documents.

## Why
Users requested ability to share PRDs in PDF format with non-technical stakeholders.

## How
- Added PDF export agent
- Uses markdown-to-pdf conversion
- Preserves formatting and styling

## Testing
- Tested with 3 different PRD formats
- Validated PDF rendering on Mac/Windows
- Checked file size and quality

## Screenshots
[Attach example PDF]
```

## 📝 Code Style Guidelines

### Markdown Files
- Use clear headers (##, ###)
- Write short paragraphs (2-4 sentences)
- Use bullet points for lists
- Include code blocks with language tags
- Add blank lines between sections

### Agent Files (.md)
- Follow existing agent structure
- Be specific in instructions
- Include examples
- Define clear success criteria
- Document expected outputs

### Templates
- Use placeholder syntax: `[description]`
- Provide examples inline
- Keep formatting consistent
- Include helpful comments

## 🎨 Content Guidelines

### Writing Style
- **Clear**: Simple language, avoid jargon
- **Concise**: No unnecessary words
- **Actionable**: Tell users what to do
- **Friendly**: Warm but professional tone

### Documentation
- Start with "why" before "how"
- Use real examples
- Include screenshots/demos
- Link to related docs

### Examples
- Should be realistic
- Cover common use cases
- Show best practices
- Include edge cases

## 🧪 Testing

### Manual Testing
Before submitting, test:
1. **Fresh install** - Test as if first-time user
2. **Happy path** - Normal use cases work
3. **Edge cases** - Error handling works
4. **Different inputs** - Various project types

### What to Test
- [ ] Command works as expected
- [ ] All phases complete successfully
- [ ] Output files are generated correctly
- [ ] Error messages are helpful
- [ ] Documentation is accurate

## 🏗️ Project Structure

```
product-planner/
├── SKILL.md              # Main entry point
├── agents/               # Agent definitions
│   ├── market-researcher.md
│   ├── competitor-analyzer.md
│   └── product-strategist.md
├── templates/            # Output templates
│   └── prd-template.md
├── examples/             # Example outputs
├── docs/                 # Additional documentation
└── README.md            # Main documentation
```

### Key Files
- **SKILL.md**: Main workflow and command definition
- **agents/*.md**: Agent instructions and prompts
- **templates/*.md**: Output document templates
- **examples/**: Complete example analyses

## 🎯 Contribution Areas

### High Priority
- [ ] Additional templates (roadmap, metrics)
- [ ] More example analyses
- [ ] Better error messages
- [ ] Performance improvements

### Medium Priority
- [ ] Additional agents (pricing, metrics)
- [ ] Custom configuration options
- [ ] Export to other formats
- [ ] Integration with tools

### Low Priority
- [ ] UI improvements
- [ ] Advanced features
- [ ] Automation scripts

## 🤝 Community Guidelines

### Be Respectful
- Treat others with kindness
- Assume positive intent
- Give constructive feedback
- Welcome newcomers

### Be Professional
- Keep discussions on topic
- No spam or self-promotion
- No inappropriate content
- Follow GitHub's terms

### Be Collaborative
- Help others when you can
- Share knowledge and resources
- Give credit where due
- Learn from feedback

## 📞 Getting Help

Stuck? Here's how to get help:

1. **Check Documentation**
   - [README](README.md)
   - [User Guide](docs/user-guide.md)
   - [FAQ](docs/faq.md)

2. **Search Issues**
   - [Existing Issues](https://github.com/kobe8cong/product-planner/issues)
   - [Closed Issues](https://github.com/kobe8cong/product-planner/issues?q=is%3Aissue+is%3Aclosed)

3. **Ask in Discussions**
   - [GitHub Discussions](https://github.com/kobe8cong/product-planner/discussions)
   - Be specific about your question
   - Provide context and examples

4. **Contact Maintainer**
   - Open an issue for project-related questions
   - For sensitive topics, email kobe8cong@users.noreply.github.com

## 🏆 Recognition

Contributors are recognized in:
- README.md Contributors section
- Release notes
- GitHub contributors page

Top contributors may be invited to:
- Become collaborators
- Join maintainer discussions
- Shape project direction

## 📜 License

By contributing, you agree that your contributions will be licensed under the MIT License.

## 🙏 Thank You!

Every contribution, big or small, makes Product Planner better. Thank you for being part of this project!

---

**Questions?** Open an [issue](https://github.com/kobe8cong/product-planner/issues) or start a [discussion](https://github.com/kobe8cong/product-planner/discussions).
