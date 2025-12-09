# .dockerignore Templates - Handover Document

## Purpose

This document serves as a comprehensive handover guide for new maintainers of the .dockerignore Templates project. It contains internal documentation, maintenance procedures, project health indicators, and operational knowledge not covered in public documentation.

## Project Structure Reference

```text
.
├── common/            # Common dockerignore templates (7 templates)
├── os/                # Operating system-specific templates (3 templates)
├── ides/              # IDE-specific dockerignore templates (4 templates)
├── tools/             # Build/deployment tool-specific templates (4 templates)
├── frameworks/        # Framework-specific dockerignore templates (40 templates)
└── languages/         # Language-specific dockerignore templates (21 templates)
```

## Technical Architecture

### Template Design Principles

1. **Comprehensive Framework Design**: Framework templates are designed to be self-contained with "everything they need" for that specific framework. They include comprehensive patterns relevant to that framework's ecosystem, including security patterns (`.env` files), dependency directories, cache files, and framework-specific artifacts.

2. **Language Templates are Language-Specific**: Language templates contain only language-specific patterns and should be combined with framework templates when working with specific frameworks.

3. **Category Templates for Specialized Needs**: Category templates (Security, Cache, Logs, etc.) are available for specialized use cases or when users want granular control over specific pattern categories, but framework templates already include comprehensive coverage for most common needs.

4. **Consistent Structure**: All templates include:
   - Header: `# Created by https://dockerignore.com/`
   - Clear section organization with comments
   - Alphabetically sorted patterns within each section for consistency and maintainability

5. **Check for Official .dockerignore Files**: Before creating or using templates, always check if the technology or framework provides an official `.dockerignore` file. Many projects include recommended `.dockerignore` patterns in their documentation or starter templates. These official patterns should be prioritized and incorporated when available.

6. **File Naming Conventions**: All template files use URL-friendly naming conventions based on official technology names:
   - **Official Names**: File names use the official technology name converted to a URL-friendly format
   - **Lowercase**: All file names are lowercase
   - **Underscore/Hyphen Separation**: Multi-word names use underscores or hyphens as appropriate (e.g., `vscode.dockerignore`, `next_js.dockerignore`)
   - **Special Characters**: Special characters like `.` are removed (e.g., `Next.js` becomes `next_js.dockerignore`)
   - **Readability**: Names are optimized for readability while maintaining consistency
   - **Examples**:
     - `Next.js` → `next_js.dockerignore` (not `next-js.dockerignore`)
     - `Visual Studio Code` → `vscode.dockerignore` (simplified)
     - `C#` → `c_sharp.dockerignore` (added underscore for readability)
     - `AdonisJS` → `adonis_js.dockerignore` (added underscore for clarity)
     - `React Native` → `react-native.dockerignore` (hyphen for space)
     - `Spring Boot` → `spring-boot.dockerignore` (hyphen for space)
     - `Android Studio` → `android-studio.dockerignore` (hyphen for space)
     - `Sublime Text` → `sublime-text.dockerignore` (hyphen for space)

7. **Pattern Categories**: Templates organize patterns into logical groups:
   - Backup and Old files
   - Build Artifacts
   - Dependency Directories
   - Docker Specific
   - Documentation
   - Environment and Security
   - IDE and Editor files
   - Log files
   - Operating System files
   - Temporary and Cache files
   - Test and Coverage Reports
   - Version Control

### Standard Template Structure

All templates in this repository follow a consistent organizational structure:

#### 1. Header Section

- Source attribution: `# Created by https://dockerignore.com/`
- Technology name and brief description
- Clear section organization with visual separators

#### 2. Technology-Specific Patterns

- Organized into logical categories with clear headers
- Patterns sorted alphabetically within each category
- Comprehensive coverage of technology-specific artifacts

#### 3. Common Patterns Reference

- References to relevant common patterns in the `common/` directory
- Examples of how to combine templates with common patterns
- Clear guidance on comprehensive coverage

#### 4. Official Sources

- Links to official Docker repositories or documentation
- Attribution for patterns based on official sources
- References to community best practices

#### 5. Usage Notes

- Important usage information and considerations
- Recommendations for production projects
- Guidance on customization and best practices

#### Visual Separators

- Use `# ============================================================================` for major section breaks
- Use `# ----------------------------------------------------------------------------` for category headers
- Use `#` for regular comments and descriptions

### Key Technical Files

1. **Node.dockerignore** (languages/): 132 lines with Node.js-specific patterns
2. **Java.dockerignore** (languages/): 69 lines with Java-specific patterns
3. **React.dockerignore** (frameworks/): 35 lines with React-specific patterns
4. **WordPress.dockerignore** (frameworks/): 71 lines with WordPress-specific patterns
5. **Drupal.dockerignore** (frameworks/): 127 lines with Drupal-specific patterns
6. **Security.dockerignore** (common/): 126 lines with security-sensitive file patterns
7. **CONTRIBUTING.md**: 396 lines with detailed contribution guidelines
8. **README.md**: 359 lines with comprehensive user documentation

### Common Patterns Across Templates

**Key Pattern Categories:**

- **High-Impact**: `.env*`, `.git/`, `*.log`, `dist/`, `build/`, `node_modules/`
- **Security-Critical**: `*.key`, `*.pem`, `*.crt`, `.secret`, `config/local.*`, `credentials.*`
- **Performance-Critical**: `**/node_modules/`, `.cache/`, `.parcel-cache`, `.turbo/`, `coverage/`

## Template Development Guidelines

### Overview

For detailed template development guidelines, quality standards, and submission processes, refer to [CONTRIBUTING.md](CONTRIBUTING.md). Key reference points for maintainers:

- **Template Requirements**: File structure, naming, content, and documentation standards
- **Template Development Guidelines**: Creating and updating templates
- **Quality Standards**: Validation checklist and review process
- **Submission Process**: How contributions are submitted and reviewed

### Using Official .dockerignore Files

#### Importance of Official Sources

**CRITICAL GUIDANCE**: When creating or updating `.dockerignore` templates, **ALWAYS check for and use official .dockerignore files from the technology's official repositories first** whenever they exist. This should be the first step in template development or updates. This ensures:

1. **Accuracy**: Official repositories contain the most up-to-date and accurate ignore patterns
2. **Best Practices**: Patterns reflect the technology's recommended practices
3. **Completeness**: Official templates include all framework/tool-specific artifacts
4. **Community Alignment**: Maintains consistency with the broader developer community

#### Sources for Official .dockerignore Files

1. **Docker Official Repositories**: Many frameworks and tools maintain official `.dockerignore` files in their Docker repositories
2. **GitHub Official Repositories**: Most frameworks and tools maintain official `.dockerignore` files in their GitHub repositories
3. **Project Documentation**: Some projects include `.dockerignore` recommendations in their documentation
4. **Starter Templates**: Official starter templates (e.g., `create-react-app`, `vue create`) often include optimal `.dockerignore` files

#### Verification Process

When using official sources:

1. **Source Attribution**: Always include a comment with the source repository URL
2. **Pattern Validation**: Verify patterns work correctly with Docker syntax
3. **Cross-Reference**: Check for overlap with common patterns in the `common/` directory
4. **Testing**: Test patterns with sample Docker builds to ensure they work as expected

#### Benefits of Official Source Integration

- **Quality Assurance**: Reduces errors and ensures comprehensive coverage
- **Maintainability**: Easier to update templates when official sources change
- **Credibility**: Increases trust in the template collection
- **Consistency**: Aligns with industry standards and best practices

### Related Projects and Guidelines

#### .gitignore Templates Collection

**Important Reference**: The [ronald2wing/.gitignores](https://github.com/ronald2wing/.gitignores) repository serves as an excellent reference and guideline for this .dockerignore templates collection. This project follows similar principles and organizational patterns that can inform our template development and maintenance practices.

**Key Learnings from .gitignore Repository**:

1. **Modular Template Structure**: Similar categorization approach with language, framework, common, OS, IDE, and tool templates
2. **Template Combination Philosophy**: Emphasis on combining multiple templates for comprehensive coverage
3. **Quality Standards**: Established guidelines for template creation, testing, and maintenance
4. **Documentation Practices**: Comprehensive documentation including CONTRIBUTING.md and AGENTS.md files
5. **Community Contribution Process**: Well-defined submission and review processes

**Recommended Practices to Adopt**:

- **Template Organization**: Maintain clear separation between language-specific, framework-specific, and common patterns
- **Combination Examples**: Provide clear examples of how to combine multiple templates
- **Testing Methodology**: Implement systematic testing of templates with real projects
- **Quality Assurance**: Establish comprehensive quality checklists for template validation
- **Documentation Standards**: Maintain consistent documentation across all templates

**Usage as Reference**: When creating or updating templates in this repository, refer to the .gitignore repository for:

- Template structure and organization patterns
- Contribution guidelines and quality standards
- Documentation practices and examples
- Community engagement and maintenance procedures

## Development Workflow

### Template Creation Process

1. **Research**: Identify common patterns for the technology
2. **Structure**: Organize into logical categories (see CONTRIBUTING.md section 4)
3. **Formatting**: Follow naming conventions (lowercase.dockerignore). Use url friendly dockerignore file names.
4. **Testing**: Validate with sample projects using Docker builds
5. **Documentation**: Add combination instructions in template header

### Testing Methodology

Key testing approaches include:

1. **Basic Validation**: `docker build --no-cache .` to verify context size reduction
2. **Pattern Testing**: Ensure excluded patterns work correctly
3. **Integration Testing**: Test template combinations
4. **Edge Cases**: Validate pattern negation and wildcards

### Version Control Strategy

1. **Branching**: Use feature branches for template additions/updates
2. **Commits**: Follow conventional commits (feat:, fix:, docs:, etc.)
3. **Tags**: Consider semantic versioning for releases
4. **Releases**: Create GitHub releases for major updates

## Quality Assurance Procedures

### Objective

Maintainers should follow established quality assurance procedures to ensure template consistency and reliability.

### Key Responsibilities

1. **Pre-Commit Validation**: Verify patterns, check for duplicates, ensure alphabetical sorting
2. **Repository Maintenance**: Regular audits, statistics tracking, pattern analysis
3. **Testing**: Sample project testing, edge case verification, cross-platform compatibility

_Note: Detailed procedures are documented in [CONTRIBUTING.md](CONTRIBUTING.md) under "Quality Standards"._

## Common Issues and Troubleshooting

### Lock File Management

**Issue**: Some templates incorrectly ignore package manager lock files.

**Solution**: Lock files (`package-lock.json`, `yarn.lock`, `pnpm-lock.yaml`, `Cargo.lock`, `composer.lock`, `Gemfile.lock`, `go.sum`, etc.) should generally be tracked in version control because:

- They ensure reproducible builds by locking exact dependency versions
- They prevent "works on my machine" issues
- They are essential for CI/CD pipelines and deployment consistency

**Exception**: Library packages where lock files might not be needed.

### Duplicate Pattern Issues

**Issue**: Duplicate patterns within the same template file.

**Solution**:

1. Use automated tools to detect duplicates
2. Remove redundant patterns while preserving functionality
3. Maintain a single instance of each pattern per file

### Framework-Specific Patterns in Language Templates

**Issue**: Language templates containing framework-specific patterns.

**Solution**:

1. Language templates should contain only language-specific patterns
2. Framework-specific patterns belong in their respective framework templates
3. Maintain clear separation of concerns between categories

### Directory Structure Changes

**Issue**: References to old directory structure (e.g., `Global/` directory).

**Solution**: Current structure uses logical categorization:

- `ides/` for code editors and IDEs
- `os/` for OS-specific files
- `tools/` for build/deployment tools (Vite, Webpack, Netlify, Vercel)

## Maintenance Procedures

### Quarterly Maintenance (Every 3 months)

1. **Template Review**: Check all 79 templates for outdated patterns
2. **Technology Updates**: Review new technologies needing templates
3. **Documentation Update**: Update README and AGENTS.md
4. **Issue Review**: Address open GitHub issues and PRs
5. **Dependency Check**: Review Docker best practices updates

### Biannual Maintenance (Every 6 months)

1. **Major Structure Review**: Evaluate template organization
2. **Performance Optimization**: Review pattern efficiency
3. **Security Audit**: Verify security-sensitive exclusions
4. **Community Feedback Analysis**: Review user suggestions

### Annual Maintenance

1. **Major Version Consideration**: Evaluate need for breaking changes
2. **License Review**: Update copyright years if needed
3. **Project Roadmap**: Plan for next year's development
4. **Infrastructure Improvements**: Consider CI/CD pipeline addition

## Repository History

### Key Historical Milestones

1. **Repository Organization**: Templates organized into logical categories (languages, frameworks, tools, editors, operating systems)
2. **Quality Standardization**: Comprehensive cleanup and standardization of all templates
3. **Pattern Optimization**: Removal of duplicate patterns and validation of Docker ignore syntax
4. **Documentation Improvement**: Creation of comprehensive handover and contribution documentation

### Comprehensive Repository Reorganization (January 2, 2026)

A comprehensive reorganization was implemented to significantly improve the repository structure, reduce duplication, and enhance maintainability:

#### 1. **Fixed Naming and Labeling Inconsistencies**

- Updated `cache.dockerignore` header from "TEMPORARY DOCKERIGNORE TEMPLATE" to "CACHE DOCKERIGNORE TEMPLATE"
- Updated `tests.dockerignore` header from "TESTING DOCKERIGNORE TEMPLATE" to "TESTS DOCKERIGNORE TEMPLATE"
- Updated `android-studio.dockerignore` header from "ANDROIDSTUDIO" to "ANDROID STUDIO"
- Updated `sublime-text.dockerignore` header from "SUBLIMETEXT" to "SUBLIME TEXT"
- Updated `docker.dockerignore` and `git.dockerignore` from "Self-contained template" to consistent category template labeling
- All category templates now use consistent labeling: "Combine with other templates as needed"

#### 2. **Fixed Reference Inconsistencies**

- Updated all references from `Temporary.dockerignore` to `Cache.dockerignore` (38 files updated)
- Updated README.md references from `Testing.dockerignore` to `Tests.dockerignore`

#### 3. **Standardized Template Headers**

- Language templates: "LANGUAGE-SPECIFIC TEMPLATE"
- Framework templates: "FRAMEWORK-SPECIFIC TEMPLATE"
- Category templates: No specific type label, consistent "Combine with other templates as needed"
- Development tools: "Self-contained template" (as they are comprehensive for their specific tool)

#### 4. **Template Modularization and Duplication Removal**

- **Removed Language/Framework Patterns from IDE Templates**:
  - `intellij.dockerignore`: Removed Python, web development, and Android build patterns that belong in language/framework templates
  - `vim.dockerignore`: Removed generic backup and bundle patterns that belong in category templates
  - `sublime.dockerignore`: Removed generic Cache/ and Backup/ patterns that belong in category templates

- **Fixed Tool Templates with Excessive Duplication**:
  - `webpack.dockerignore`: Reduced from extensive duplication to only Webpack-specific patterns
  - `vite.dockerignore`: Reduced from extensive duplication to only Vite-specific patterns
  - `netlify.dockerignore`: Reduced from extensive duplication to only Netlify-specific patterns
  - `vercel.dockerignore`: Reduced from extensive duplication to only Vercel-specific patterns

- **Standardized Template Labeling**:
  - **IDE Templates**: Now labeled as "IDE-SPECIFIC TEMPLATE" with clear combination instructions
  - **Tool Templates**: Now labeled as "TOOL-SPECIFIC TEMPLATE" with clear combination instructions
  - **Category Templates**: Now labeled as "CATEGORY TEMPLATE" with clear combination instructions

#### 5. **Benefits of Reorganization**

- **Significantly Reduced Duplication**: Common patterns now centralized in `common/` directory
- **Improved Maintainability**: Updates to common patterns propagate to all referencing templates
- **Enhanced Consistency**: Standardized approach across all 79 template files
- **Better User Experience**: Clearer organization and combination guidance
- **Modern Pattern Coverage**: Comprehensive categories for security, logs, cache, backup, and testing

#### 6. **Updated Repository Statistics**

- **Total Templates**: 79 dockerignore files
- **Common Patterns**: 7 templates in `common/` directory
- **Language Templates**: 21 templates in `languages/` directory
- **Framework Templates**: 40 templates in `frameworks/` directory
- **Tool Templates**: 4 templates in `tools/` directory
- **Editor Templates**: 4 templates in `ides/` directory
- **Operating System Templates**: 3 templates in `os/` directory

#### 7. **Template Types and Their Purposes**

- **Language Templates** (`languages/`): Contain ONLY language-specific patterns
- **Framework Templates** (`frameworks/`): Contain ONLY framework-specific patterns
- **Category Templates** (`common/`): Contain comprehensive patterns for specific categories (Security, Cache, Logs, etc.)
- **IDE Templates** (`ides/`): Contain ONLY IDE-specific patterns
- **Tool Templates** (`tools/`): Contain ONLY tool-specific patterns

#### 8. **Usage Example**

```bash
# Complete coverage for a Node.js + React + Vite + VSCode project
cat languages/Node.dockerignore \
    frameworks/React.dockerignore \
    tools/Vite.dockerignore \
    ides/VSCode.dockerignore \
    common/Security.dockerignore \
    common/Cache.dockerignore \
    common/Logs.dockerignore \
    common/Backup.dockerignore \
    os/Linux.dockerignore \
    os/macOS.dockerignore \
    os/Windows.dockerignore > .dockerignore
```

This modular approach allows users to create precise `.dockerignore` files tailored to their exact technology stack while maintaining consistency and avoiding duplication.

## Post-Reorganization Status

Following the comprehensive reorganization completed in January 2026, the repository structure has been significantly improved with:

- **Reduced duplication**: Common patterns centralized in the `common/` directory
- **Improved maintainability**: Updates to common patterns propagate to all referencing templates
- **Enhanced consistency**: Standardized approach across all 79 template files
- **Better user experience**: Clearer organization and combination guidance
- **Modern pattern coverage**: Comprehensive categories for security, logs, cache, backup, and testing

### Ongoing Maintenance Considerations

Maintainers should periodically review templates for:

1. **Template scope consistency**: Ensure framework templates contain only framework-specific patterns
2. **Pattern accuracy**: Verify patterns work correctly with current Docker versions
3. **Technology updates**: Add templates for new technologies as they gain popularity
4. **Documentation alignment**: Keep AGENTS.md, README.md, and CONTRIBUTING.md synchronized

Refer to the [Quality Standards](CONTRIBUTING.md#quality-standards) section in CONTRIBUTING.md for detailed maintenance procedures.

## Community Management

### Communication Channels

- **Primary**: GitHub Issues for bug reports
- **Secondary**: GitHub Discussions for community questions
- **Emergency**: Security advisories for critical vulnerabilities

### Communication Plan

- **Bugs**: GitHub issues with `bug` label
- **Security**: GitHub security advisories
- **Community**: GitHub Discussions for general questions, feature requests, and community
