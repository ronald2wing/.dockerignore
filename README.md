# .dockerignore Templates

A comprehensive collection of `.dockerignore` templates for various programming languages, frameworks, and tools. This repository provides ready-to-use templates to help you optimize your Docker builds by excluding unnecessary files from the build context.

## Table of Contents

- [What is a .dockerignore file?](#what-is-a-dockerignore-file)
- [Why Use .dockerignore?](#why-use-dockerignore)
- [Installation](#installation)
- [Usage](#usage)
- [Folder Structure](#folder-structure)
- [What Makes a Good Template?](#what-makes-a-good-template)
- [Versioned Templates](#versioned-templates)
- [Specialized Templates](#specialized-templates)
- [Best Practices](#best-practices)
- [FAQ](#faq)
- [Contributing](#contributing)
- [Project Overview](#project-overview)
- [Related Projects](#related-projects)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## What is a .dockerignore file?

A `.dockerignore` file is similar to a `.gitignore` file but is used by Docker during the build process. It specifies which files and directories should be excluded from the Docker build context, which can significantly reduce build time and image size.

## Why Use .dockerignore?

When building Docker images, the entire build context (all files in the directory) is sent to the Docker daemon. This can be slow and inefficient, especially when your project contains:

- Build artifacts and cache directories
- Development dependencies (`node_modules/`, `vendor/`)
- IDE configuration and OS metadata
- Log files and temporary files
- Sensitive environment files
- Test files and coverage reports

Using a `.dockerignore` file helps you exclude these unnecessary files, resulting in:

- **Better caching** - More efficient layer caching by excluding volatile files
- **Faster build times** - Smaller context means less data to transfer
- **Improved security** - Sensitive files never reach the build context
- **Smaller image sizes** - No unnecessary files included in final layers

## Installation

### Quick Download

Download templates directly using curl:

```bash
# For a Node.js project
curl -o .dockerignore https://raw.githubusercontent.com/ronald2wing/dockerignore/master/languages/node.dockerignore

# For a Python project
curl -o .dockerignore https://raw.githubusercontent.com/ronald2wing/dockerignore/master/languages/python.dockerignore

# For a React project
curl -o .dockerignore https://raw.githubusercontent.com/ronald2wing/dockerignore/master/frameworks/react.dockerignore

# For a Spring Boot project
curl -o .dockerignore https://raw.githubusercontent.com/ronald2wing/dockerignore/master/frameworks/springboot.dockerignore
```

### Alternative Methods

You can also clone the repository or use it as a submodule:

```bash
# Clone the repository
git clone https://github.com/ronald2wing/dockerignore.git

# Or use as a submodule
git submodule add https://github.com/ronald2wing/dockerignore.git
```

## Usage

### Basic Usage

1. **Check for official .dockerignore files**: Before using templates, verify if the technology or framework has an official `.dockerignore` file. Official patterns from project documentation or starter templates should be prioritized when available.

2. **Choose the appropriate template** from the `languages/`, `frameworks/`, `common/`, `os/`, `ides/`, or `tools/` directories
3. **Copy the contents** into your project's `.dockerignore` file
4. **Customize as needed** for your specific project requirements

### Combining Templates

The modular template system allows you to combine templates based on your project's specific needs. Follow this recommended approach:

1. **Start with language template** - Choose the appropriate language template from `languages/`
2. **Add framework template** - If using a framework, add the corresponding template from `frameworks/`
3. **Include common templates** - Add relevant common templates from `common/` for complete coverage
4. **Add operating system templates** - Include OS-specific templates from `os/` if needed
5. **Add IDE templates** - Include templates for your development environment from `ides/`
6. **Add tool templates** - Include templates for build/deployment tools from `tools/`

#### Common Combination Examples

```bash
# Example 1: Node.js + React + Vite + VSCode Project (Modern Web Development)
cat languages/node.dockerignore \
    frameworks/react.dockerignore \
    tools/vite.dockerignore \
    ides/vscode.dockerignore \
    common/security.dockerignore \
    common/cache.dockerignore \
    common/logs.dockerignore \
    common/backup.dockerignore \
    os/linux.dockerignore \
    os/macos.dockerignore \
    os/windows.dockerignore > .dockerignore

# Example 2: Python + Django + PostgreSQL Project (Backend API)
cat languages/python.dockerignore \
    frameworks/django.dockerignore \
    common/security.dockerignore \
    common/cache.dockerignore \
    common/logs.dockerignore \
    common/backup.dockerignore \
    os/linux.dockerignore \
    os/macos.dockerignore \
    os/windows.dockerignore > .dockerignore

# Example 3: Java + Spring Boot + Maven Project (Enterprise)
cat languages/java.dockerignore \
    frameworks/springboot.dockerignore \
    common/security.dockerignore \
    common/cache.dockerignore \
    common/logs.dockerignore \
    common/backup.dockerignore \
    os/linux.dockerignore \
    os/macos.dockerignore \
    os/windows.dockerignore \
    ides/intellij.dockerignore > .dockerignore

# Example 4: Minimal Node.js Project (Essential Only)
cat languages/node.dockerignore \
    common/security.dockerignore \
    common/cache.dockerignore > .dockerignore
```

**Tip**: Use `sort -u` to remove duplicate patterns: `cat template1 template2 | sort -u > .dockerignore`

**Important**: The modular template system allows you to create precise `.dockerignore` files tailored to your exact technology stack. Start with the essential templates (language + security) and add only what you need for your specific project.

## Folder Structure

We support a collection of templates, organized in this way:

```text
.
├── languages/          # Language-specific templates (21 templates)
│   ├── node.dockerignore      # Node.js specific patterns
│   ├── python.dockerignore    # Python specific patterns
│   ├── java.dockerignore      # Java specific patterns
│   └── ... (18 more)
├── frameworks/         # Framework-specific templates (40 templates)
│   ├── react.dockerignore     # React specific patterns
│   ├── django.dockerignore    # Django specific patterns
│   ├── springboot.dockerignore # Spring Boot specific patterns
│   └── ... (37 more)
├── common/            # Common templates for cross-cutting concerns (7 templates)
│   ├── security.dockerignore  # Security-sensitive files
│   ├── logs.dockerignore      # Log files
│   ├── cache.dockerignore     # Temporary and cache files
│   └── ... (5 more)
├── os/                # Operating system templates (3 templates)
│   ├── linux.dockerignore     # Linux-specific files
│   ├── macos.dockerignore     # macOS-specific files
│   └── windows.dockerignore   # Windows-specific files
├── ides/              # IDE templates (4 templates)
│   ├── vscode.dockerignore    # VSCode-specific files
│   ├── intellij.dockerignore  # IntelliJ/IDEA-specific files
│   └── ... (2 more)
└── tools/             # Build/deployment tool templates (4 templates)
    ├── vite.dockerignore      # Vite-specific files
    ├── webpack.dockerignore   # Webpack-specific files
    └── ... (2 more)
```

### Template Types

- **Language Templates** (`languages/`): Language-specific patterns only (Node.js, Python, Java, Go, Rust, etc.)
- **Framework Templates** (`frameworks/`): Framework-specific patterns only (React, Django, Spring Boot, etc.)
- **Common Templates** (`common/`): Cross-cutting concerns (Security, Logs, Cache, Backup, etc.)
- **Operating System Templates** (`os/`): OS-specific patterns (Linux, macOS, Windows)
- **IDE Templates** (`ides/`): IDE-specific patterns (VSCode, IntelliJ, Vim, Sublime)
- **Tool Templates** (`tools/`): Build/deployment tool-specific patterns (Vite, Webpack, Netlify, Vercel)

## What Makes a Good Template?

A template should contain a set of rules to help Docker builds work with a specific programming language, framework, tool or environment.

If it's not possible to curate a small set of useful rules for this situation, then the template is not a good fit for this collection.

If a template is mostly a list of files installed by a particular version of some software (e.g. a PHP framework), it could live as a specialized template. See [Specialized Templates](#specialized-templates) for more details.

If you have a small set of rules, or want to support a technology that is not widely in use, and still believe this will be helpful to others, please read the section about [Specialized Templates](#specialized-templates) for more details.

Include details when opening pull request if the template is important and visible. We may not accept it immediately, but we can promote it to the main directories at a later date based on interest.

Please also understand that we can't list every tool that ever existed. Our aim is to curate a collection of the *most common and helpful* templates, not to make sure we cover every project possible. If we choose not to include your language, tool, or project, it's not because it's not awesome.

## Versioned Templates

Some templates can change greatly between versions, and if you wish to contribute to this repository we need to follow this specific flow:

- The template in the main directories should be the current supported version
- The template in the main directories should not have a version in the filename (i.e. "evergreen")
- Previous versions of templates should be considered for deprecation or updating
- Version-specific patterns should be documented in comments within the template

This helps ensure users get the latest version (because they'll use whatever is in the main directories) but helps maintainers support evolving patterns.

## Specialized Templates

If you have a template that you would like to contribute, but it isn't quite mainstream, please consider whether it fits into one of our existing categories:

- **Language Templates** (`languages/`): For programming language-specific patterns
- **Framework Templates** (`frameworks/`): For framework-specific patterns
- **Common Templates** (`common/`): For cross-cutting concerns
- **Operating System Templates** (`os/`): For OS-specific patterns
- **IDE Templates** (`ides/`): For IDE-specific patterns
- **Tool Templates** (`tools/`): For build/deployment tool-specific patterns

The rules in your specialized template should be specific to the framework or tool, and any additional templates should be mentioned in a comment in the header of the template.

For example, a specialized template might include:

```dockerignore
# Created by https://dockerignore.com/
# Specialized template for [Technology Name]
# website: https://example.com/
#
# Recommended combination: LanguageTemplate.dockerignore + Common/Security.dockerignore

# Technology-specific patterns
pattern1/
pattern2/
*.ext
```

## Best Practices

### 1. Customize for Your Project

Add project-specific exclusions for:

- Build artifacts and temporary files
- Database dumps and backups
- Large media files
- Sensitive files (API keys, certificates, credentials)

### 2. Test and Validate

Ensure your `.dockerignore` file works correctly:

- Run `docker build --no-cache` to see what's being sent to the daemon
- Verify essential files are not accidentally excluded
- Check build outputs are correct

### 3. Maintain and Update

Keep your `.dockerignore` file current:

- Review periodically as your project evolves
- Add patterns for new tools and dependencies
- Remove patterns for tools no longer used
- Document patterns with comments for future maintainers

### 4. Pattern Ordering

Place more specific patterns before general ones. Docker processes patterns in order, and the first matching pattern wins.

## FAQ

### Q: Can I have multiple .dockerignore files?

A: No, Docker only recognizes one `.dockerignore` file in the build context root.
However, you can combine multiple templates into one file using the `cat` command
as shown in the examples.

### Q: Can I use .gitignore as .dockerignore?

A: While similar, `.gitignore` and `.dockerignore` serve different purposes.
Some patterns may overlap, but `.dockerignore` should be more comprehensive
for build-time exclusions. `.dockerignore` should exclude more files like
build artifacts, dependencies, and temporary files that aren't typically
committed to git but are present during development.

### Q: Can I use environment variables in .dockerignore?

A: No, `.dockerignore` doesn't support environment variable expansion. It's a
static file that's processed before any build arguments or environment variables
are evaluated.

### Q: How do I handle files that need to be excluded in development but included in production?

A: Use conditional logic in your Dockerfile or create separate `.dockerignore`
files for different environments. You can also use build arguments to control
what gets copied.

### Q: Should I exclude package-lock.json or yarn.lock?

A: Generally yes, as these are used during development but the actual
dependencies are installed from package.json during `npm install` or
`yarn install` in the Dockerfile. However, if you want reproducible builds,
you might want to include lock files and use `npm ci` instead of `npm install`.

### Q: What about .dockerignore in subdirectories?

A: Docker only looks for `.dockerignore` in the build context root (the directory
specified in the `docker build` command). Patterns in `.dockerignore` apply to
all files and directories in the build context, regardless of their depth.

### Q: What about Docker multi-stage builds?

A: `.dockerignore` applies to the initial build context sent to the Docker daemon.
In multi-stage builds, it helps reduce the initial context size. Note that
files copied between stages using `COPY --from` are not affected by `.dockerignore`
since they come from previous build stages, not the build context.

## Contributing

We welcome contributions! Please see our comprehensive [CONTRIBUTING.md](CONTRIBUTING.md) guide for detailed instructions on:

- Code of conduct and community guidelines
- How to contribute new templates or improve existing ones
- Submission and review process
- Template guidelines and quality standards
- Testing requirements and methodology

For complete contribution guidelines, please refer to [CONTRIBUTING.md](CONTRIBUTING.md).

## Project Overview

**Total Templates:** 79
**Language Templates:** 21 (Bun, CSharp, Dart, Deno, Elixir, Go, Haskell, Java, JavaScript, Kotlin, Lua, Node.js, PHP, Perl, Python, Ruby, Rust, Scala, Swift, TypeScript, Zig)
**Framework Templates:** 40 (AdonisJS, Angular, Astro, CakePHP, CodeIgniter, Django, DotNet, Drupal, Electron, Express, FastAPI, Flask, Flutter, Gatsby, Ghost, Hapi, Ionic, Joomla, Koa, Laravel, Magento, NestJS, Next.js, Nuxt.js, Phoenix, Qwik, Rails, React, ReactNative, Remix, SolidJS, Spring Boot, Strapi, Svelte, SvelteKit, Symfony, TanStack, Tauri, Vue, WordPress)
**Common Templates:** 7 (Backup, Cache, Docker, Git, Logs, Security, Tests)
**Operating System Templates:** 3 (Linux, macOS, Windows)
**IDE Templates:** 4 (IntelliJ, Sublime, Vim, VSCode)
**Tool Templates:** 4 (Netlify, Vercel, Vite, Webpack)

**License:** MIT License
**Repository:** <https://github.com/ronald2wing/dockerignore>

## Related Projects

- [Awesome Docker](https://github.com/veggiemonk/awesome-docker) - A curated list of Docker resources
- [Docker Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/) - Official Docker best practices
- [Docker documentation on .dockerignore](https://docs.docker.com/engine/reference/builder/#dockerignore-file)
- [GitHub gitignore templates](https://github.com/github/gitignore)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE)
file for details.

## Acknowledgments

- All contributors who have helped improve these templates
- Community contributions from developers worldwide
- The Docker community for best practices and patterns
- The GitHub gitignore templates project for inspiration
