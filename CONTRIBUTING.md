# Contributing to .dockerignore Templates

Thank you for your interest in contributing to the dockerignore Templates project! This document provides guidelines and instructions for contributing new templates, improving existing ones, and participating in the community.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Types of Contributions](#types-of-contributions)
- [Template Guidelines](#template-guidelines)
- [Testing Your Template](#testing-your-template)
- [Submission Process](#submission-process)
- [Review Process](#review-process)
- [Quality Assurance Checklist](#quality-assurance-checklist)
- [Maintenance and Updates](#maintenance-and-updates)
- [Getting Help](#getting-help)

## Code of Conduct

We are committed to providing a friendly, safe, and welcoming environment for all contributors. By participating in this project, you agree to:

- Be respectful and inclusive in your language and actions
- Focus on what is best for the community and project
- Provide constructive feedback and accept it gracefully
- Show empathy towards other community members

Unacceptable behavior includes, but is not limited to:

- Any conduct that could reasonably be considered inappropriate in a professional setting
- Harassment, discrimination, or personal attacks
- Publishing others' private information without permission
- Trolling, insulting, or derogatory comments

## Getting Started

### Prerequisites

- Basic understanding of the programming language or framework you're creating a template for
- Familiarity with Docker and `.dockerignore` syntax
- Git and GitHub account

### Setting Up Your Development Environment

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:

   ```bash
   git clone https://github.com/YOUR-USERNAME/dockerignore.git
   cd dockerignore
   ```

3. **Create a new branch** for your contribution:

   ```bash
   git checkout -b feature/new-template-name
   ```

### Project Structure

For detailed project structure information, refer to the [Project Structure Reference](AGENTS.md#project-structure-reference) or the [Folder Structure](README.md#folder-structure) section in the README.

## Types of Contributions

We welcome several types of contributions:

1. **New Templates**: Create templates for new languages, frameworks, or tools
2. **Template Improvements**: Update existing templates with better patterns or organization
3. **Bug Fixes**: Correct errors in existing templates
4. **Documentation**: Improve README, CONTRIBUTING.md, or other documentation
5. **Testing**: Test templates with real projects and report issues

## Template Guidelines

### File Naming Convention

All template files use URL-friendly naming conventions based on official technology names:

- **Official Names**: File names use the official technology name converted to a URL-friendly format
- **Lowercase**: All file names are lowercase
- **Underscore/Hyphen Separation**: Multi-word names use underscores or hyphens as appropriate (e.g., `vscode.dockerignore`, `next_js.dockerignore`)
- **Special Characters**: Special characters like `.` are removed (e.g., `Next.js` becomes `next_js.dockerignore`)
- **Readability**: Names are optimized for readability while maintaining consistency
- **Examples**:
  - `Next.js` → `next_js.dockerignore` (not `next-js.dockerignore`)
  - `Visual Studio Code` → `vscode.dockerignore` (simplified)
  - `C#` → `c_sharp.dockerignore` (added underscore for readability)
  - `AdonisJS` → `adonisjs.dockerignore` (JS suffix as part of official name)
  - `React Native` → `react-native.dockerignore` (hyphen for space)
  - `Spring Boot` → `spring-boot.dockerignore` (hyphen for space)
  - `Android Studio` → `android-studio.dockerignore` (hyphen for space)
  - `Sublime Text` → `sublime-text.dockerignore` (hyphen for space)

### Required Header

Every template must start with:

```dockerignore
# Created by https://dockerignore.com/
```

### Template Structure

All templates should follow this consistent structure:

```dockerignore
# Created by https://dockerignore.com/

# [CATEGORY NAME]
# Brief description of what this category excludes
pattern1/
pattern2/
*.ext

# [ANOTHER CATEGORY]
# Brief description
**/directory/
file.*
```

### Pattern Organization

Organize patterns into logical categories. Common categories include:

1. **Build Artifacts** (`dist/`, `build/`, `target/`, `out/`)
2. **Cache Directories** (`.cache/`, `.parcel-cache`, `.turbo/`)
3. **Development Dependencies** (`node_modules/`, `vendor/`, `.venv/`)
4. **Environment Files** (`.env`, `.env.*`, `*.key`, `*.pem`)
5. **IDE Files** (`.idea/`, `.vscode/`, `.sublime-*`)
6. **Log Files** (`*.log`, `logs/`, `*.pid`)
7. **OS Metadata** (`.DS_Store`, `Thumbs.db`, `desktop.ini`)
8. **Temporary Files** (`tmp/`, `temp/`, `*.tmp`, `*.cache`)
9. **Test Outputs** (`coverage/`, `test-results/`, `.nyc_output`)

### Pattern Classification Guidelines

To maintain a modular architecture and avoid duplication, follow these guidelines for classifying patterns:

#### Language Templates (`languages/`)

Language templates should contain **only language-specific patterns**, such as:

- Language-specific build artifacts (e.g., `*.pyc`, `*.class`, `*.o`)
- Language-specific dependency directories (e.g., `node_modules/`, `vendor/`, `.venv/`)
- Language-specific cache directories (e.g., `.cache/`, `.parcel-cache/`, `.turbo/`)
- Language-specific configuration files (e.g., `package-lock.json`, `yarn.lock`, `Cargo.lock`)
- Language-specific test outputs (e.g., `coverage/`, `.nyc_output/`)
- Language-specific IDE configuration files (e.g., `.idea/` for IntelliJ, `.vscode/` for VS Code)

#### Framework Templates (`frameworks/`)

Framework templates should contain **only framework-specific patterns**, such as:

- Framework-specific build artifacts (e.g., `.next/` for Next.js, `dist/` for React)
- Framework-specific configuration files (e.g., `angular.json`, `nuxt.config.*`)
- Framework-specific cache directories (e.g., `.nuxt/` for Nuxt.js)
- Framework-specific temporary files (e.g., `*.pid.lock`, `*.seed`)
- Framework-specific log files (e.g., `fastapi.log`, `uvicorn.log`)
- Framework-specific development server files (e.g., `.svelte-kit/`, `.astro/`)

#### Common Templates (`common/`)

Common templates contain **cross-cutting concerns**, such as:

- Operating system files (`.DS_Store`, `Thumbs.db`)
- Security-sensitive files (`.env*`, `*.key`, `*.pem`)
- Log files (`*.log`, `logs/`)
- Temporary and cache files (`tmp/`, `temp/`, `*.tmp`)
- Backup and old files (`*.bak`, `*.old`, `*.backup`)
- Version control files (`.git/`, `.gitignore`, `.gitattributes`)

#### IDE Templates (`ides/`)

IDE templates should contain **only IDE-specific patterns**, such as:

- IDE-specific configuration directories (e.g., `.idea/`, `.vscode/`, `.sublime-*`)
- IDE-specific cache files (e.g., `*.sublime-workspace`, `.vs/`)
- IDE-specific project files (e.g., `*.code-workspace`, `*.iml`)

#### Tool Templates (`tools/`)

Tool templates should contain **only tool-specific patterns**, such as:

- Build tool artifacts (e.g., `webpack-assets.json`, `vite.config.*`)
- Deployment platform files (e.g., `.netlify/`, `.vercel/`)
- Development server files (e.g., `.parcel-cache/`, `.turbo/`)

#### OS Templates (`os/`)

OS templates should contain **only operating system-specific patterns**, such as:

- macOS files (`.DS_Store`, `._*`, `.Spotlight-V100`, `.Trashes`)
- Windows files (`Thumbs.db`, `desktop.ini`, `*.lnk`)
- Linux files (`.directory`, `lost+found/`)

#### Avoiding Duplication

- **DO NOT** include language patterns in framework templates
- **DO NOT** include category patterns in language or framework templates
- **DO NOT** include IDE patterns in language templates
- **DO** reference the appropriate language template in framework template headers
- **DO** combine templates for complete coverage (e.g., `Node.dockerignore + React.dockerignore + Security.dockerignore + VSCode.dockerignore`)

#### Example Classification

- **Node.js language patterns** (in `Node.dockerignore`): `node_modules/`, `.npm/`, `package-lock.json`, `.eslintcache`
- **React framework patterns** (in `React.dockerignore`): `.cra/`, `.storybook/`, `storybook-static/`
- **Security category patterns** (in `Security.dockerignore`): `.env*`, `*.key`, `*.pem`, `.secret`
- **VS Code IDE patterns** (in `VSCode.dockerignore`): `.vscode/`, `*.code-workspace`
- **Vite tool patterns** (in `Vite.dockerignore`): `vite.config.*`, `.vite/`

### Pattern Syntax Best Practices

- Add comments for clarity when needed
- Avoid duplicate patterns
- Group related patterns together
- Order patterns from specific to general
- Use `**/` for recursive directory matching (e.g., `**/node_modules/`)
- Use `*` for wildcards within a single directory level
- Use consistent indentation and spacing

### Security Considerations

Always exclude security-sensitive files:

```dockerignore
# Certificate and key files
*.cert
*.crt
*.key
*.pem
*.priv

# Environment and configuration files
.env
.env.*
.secret
.secrets

# Local configuration files
config/local.*
config/secret.*
credentials.*
```

### Common Pattern Examples

```dockerignore
# Exclude directory at any level
**/node_modules/

# Exclude multiple patterns
dist/
build/
out/

# Exclude specific file types
*.log
*.tmp

# Exclude with wildcards
*.log.*
test-*.txt

# Exclude but include specific file
*.env
!.env.example
```

## Testing Your Template

### Testing Methodology

1. **Create a test project** using the language/framework you're creating a template for
2. **Copy your template** to the test project as `.dockerignore`
3. **Test with Docker build** to ensure it works correctly:

```bash
# Navigate to your test project
cd test-project

# Test the build
docker build --no-cache --progress=plain .
```

### What to Test

- **Build succeeds**: The Docker build should complete without errors
- **Correct exclusions**: Verify that unnecessary files are excluded
- **Essential files included**: Ensure necessary build files are not excluded
- **Pattern accuracy**: Check that patterns work as expected
- **Performance**: The build context should be significantly smaller with `.dockerignore`

### Test Scenarios

Test with different project structures:

- Simple project structure
- Nested directories
- Multiple build configurations
- Different dependency managers

## Submission Process

### 1. Create Your Template

- Ensure it follows all template guidelines
- Follow the naming convention
- Place your template in the appropriate directory (`languages/`, `frameworks/`, `common/`, `os/`, `ides/`, or `tools/`)

### 2. Update Documentation (If Needed)

If you're adding a new template category or making significant changes:

- Update the README.md to reflect the new template
- Update the template count and statistics
- Add any new usage examples

### 3. Commit Your Changes

```bash
# Add your template file
git add languages/YourLanguage.dockerignore

# Commit with a descriptive message
git commit -m "feat: add YourLanguage.dockerignore template

- Add comprehensive patterns for YourLanguage projects
- Follow template structure and organization guidelines
- Include patterns for build artifacts, dependencies, and IDE files"
```

### 4. Push to Your Fork

```bash
git push origin feature/new-template-name
```

### 5. Create a Pull Request

1. Go to the original repository on GitHub
2. Click "New Pull Request"
3. Select your fork and branch
4. Fill in the pull request template:

### Pull Request Template

```markdown
## Summary

Brief description of what this PR adds or changes.

## Changes

- Added `languages/YourLanguage.dockerignore` template
- Updated README.md documentation
- [Other changes...]

## Testing

- Tested with [specific project type]
- Confirmed essential files are not excluded
- Verified build succeeds with template
- [Other testing details...]

## Checklist

- [ ] Header `# Created by https://dockerignore.com/` is present
- [ ] No duplicate patterns
- [ ] Patterns are organized into logical categories
- [ ] Security-sensitive files are properly excluded
- [ ] Template follows consistent structure and format
- [ ] Tested with real projects
- [ ] Documentation updated if needed
```

## Review Process

### Review Timeline

- Initial review within 3-5 business days
- Feedback and requested changes
- Final review and merge

### What Reviewers Look For

1. **Template Quality**:
   - Follows established structure and format
   - Organized logically with clear categories
   - Patterns are comprehensive and accurate

2. **Technical Accuracy**:
   - No essential files are excluded
   - Patterns work correctly with Docker
   - Security considerations are addressed

3. **Testing**:
   - Template has been tested with real projects
   - Build succeeds with the template
   - Performance improvements are demonstrated

### Addressing Feedback

If reviewers request changes:

1. Make the requested changes in your branch
2. Push the updates to your fork
3. The pull request will automatically update
4. Respond to comments to let reviewers know changes are complete

## Quality Assurance Checklist

For detailed quality assurance guidelines, refer to the [Quality Assurance Checklist](AGENTS.md#quality-assurance-checklist). Key quality standards include:

- [ ] Header `# Created by https://dockerignore.com/` is present
- [ ] No duplicate patterns exist
- [ ] Patterns are organized into logical categories
- [ ] Security-sensitive files are properly excluded
- [ ] Template follows the consistent structure and format
- [ ] Template has been tested with real projects
- [ ] No essential build files are accidentally excluded

## Maintenance and Updates

### Keeping Templates Current

As technologies evolve, templates may need updates. Consider updating templates when:

- Common patterns change in the ecosystem
- New build tools or package managers are released
- New IDE or development tools become popular
- Security best practices evolve

### Reporting Issues with Existing Templates

If you find issues with existing templates:

1. **Check if an issue already exists** on GitHub
2. **Create a new issue** with details:
   - Template name and path
   - Description of the issue
   - Expected behavior
   - Actual behavior
   - Steps to reproduce
   - Any relevant error messages
3. **Optionally, submit a fix** by following the contribution process

### Finding Issues to Work On

- Check the [GitHub Issues](https://github.com/ronald2wing/dockerignore/issues) for open issues
- Look for issues labeled `good-first-issue` or `help-wanted`
- Review existing templates for potential improvements

## Getting Help

- **Documentation**: Check README.md and AGENTS.md for project information
- **GitHub Issues**: For bug reports and feature requests
- **Pull Requests**: For contributing code and templates

### Staying Updated

- **Watch the repository** to get notifications of new issues and pull requests
- **Follow releases** to see new templates and updates
- **Star the repository** to show your support

### Recognition

All contributors are recognized in:

- GitHub's contributor graph
- Release notes for major versions
- The project's README.md (for significant contributions)

## License

By contributing to this project, you agree that your contributions will be licensed under the project's [MIT License](LICENSE).

---

Thank you for contributing to the dockerignore Templates project! Your efforts help make Docker builds faster and more secure for developers worldwide.
