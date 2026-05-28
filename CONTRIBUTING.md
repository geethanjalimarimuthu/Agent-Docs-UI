# Contributing

Thank you for interest in contributing to Polaris AI Agents UI!

## How to Contribute

### Report Bugs

1. Go to [GitHub Issues](https://github.com/IN-ATOS-AARA/atos-ai-agents-ui/issues)
2. Click **New Issue**
3. Provide:
   - Clear title
   - Steps to reproduce
   - Expected behavior
   - Actual behavior
   - Screenshots (if applicable)
   - Browser/OS details

### Suggest Improvements

1. Open a GitHub Issue with label `enhancement`
2. Describe the desired feature
3. Explain the use case
4. Provide examples

### Improve Documentation

1. Fork the repository
2. Edit files in the `docs/` folder
3. Test locally (see below)
4. Submit a pull request

### Contribute Code

1. Create a feature branch
2. Follow code style (run `npm run lint`)
3. Add/update tests
4. Update relevant docs
5. Submit pull request with description

## Development Setup

### Clone & Install

```bash
git clone https://github.com/IN-ATOS-AARA/atos-ai-agents-ui.git
cd atos-ai-agents-ui
npm install
```

### Local Development

```bash
# Start dev server
npm run dev

# Run linter
npm run lint

# Build for production
npm run build

# Test production build
npm run preview
```

### Component Development

```bash
# Start Storybook
npm run dev:storybook
```

## Documentation Style Guide

### File Organization

```
docs/
├── index.md                      # Homepage
├── getting-started.md            # First steps
├── quick-reference.md            # Cheat sheet
├── faq.md                        # Q&A
├── api.md                        # API Reference
├── guides/
│   ├── index.md
│   ├── agent-management.md
│   ├── visual-editor.md
│   ├── settings.md
│   └── best-practices.md
└── _config.yml                   # Jekyll config
```

### Markdown Style

1. **Use clear headings**
   ```markdown
   # Main Title
   ## Section
   ### Subsection
   ```

2. **Include code blocks**
   ```markdown
   ```bash
   npm install
   ```
   ```

3. **Add tables for comparisons**
   ```markdown
   | Column 1 | Column 2 |
   |----------|----------|
   | Value    | Value    |
   ```

4. **Use callouts**
   ```markdown
   ✅ Good practice
   ❌ Bad practice
   ⚠️ Warning
   ```

5. **Link to other docs**
   ```markdown
   [Link text](../path/to/file.md)
   ```

### Frontmatter

All pages should include Jekyll frontmatter:

```yaml
---
layout: default
title: Page Title
nav_order: 1
parent: Parent Page (optional)
---
```

### Tone & Voice

- Write for users, not developers (unless technical section)
- Use active voice
- Keep sentences short
- Use examples frequently
- Avoid jargon; explain if necessary

## Testing Documentation Locally

### With Jekyll

```bash
# Install Jekyll (one time)
gem install jekyll bundler

# Build and serve
cd docs
jekyll serve --baseurl="/atos-ai-agents-ui"

# Open http://localhost:4000/atos-ai-agents-ui
```

### Without Jekyll (simple approach)

Use a local HTTP server:

```bash
cd docs
python3 -m http.server 8000

# Open http://localhost:8000/index.html
```

## Pull Request Process

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Make changes
4. Test locally
5. Commit with clear messages: `git commit -m "Add feature X"`
6. Push to your fork
7. Open Pull Request on GitHub
8. Provide clear description of changes
9. Reference any related issues: `Fixes #123`

### PR Checklist

- [ ] Code follows style guide (run `npm run lint`)
- [ ] Documentation is updated
- [ ] Changes are tested
- [ ] Commit messages are clear
- [ ] No sensitive data committed

## Code Style

### TypeScript

- Use strict mode
- Add type annotations
- Avoid `any` types
- Use const by default

### Components

- Use functional components
- Use React hooks
- Document with JSDoc comments
- Include Storybook stories

### Naming Conventions

- Components: `PascalCase` (e.g., `AgentComponent`)
- Functions: `camelCase` (e.g., `handleSubmit`)
- Constants: `UPPER_SNAKE_CASE` (e.g., `MAX_ITERATIONS`)
- Files: Match export name or use kebab-case

## Commit Message Guidelines

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation only
- `style`: Formatting, missing semicolons, etc.
- `refactor`: Code refactoring
- `perf`: Performance improvements
- `test`: Adding tests
- `chore`: Build, dependencies, etc.

### Examples

```
feat(agent): add save as version functionality
fix(editor): correct node connection validation
docs(getting-started): clarify model selection step
```

## License

By contributing, you agree that your contributions will be licensed under the same license as the project (Proprietary – Atos 2025).

## Questions?

- 📖 Check [documentation](/)
- 💬 Open a GitHub discussion
- 📧 Email: dl-atospolarisaisupport@atos.net

---

Thank you for contributing to Polaris AI!
