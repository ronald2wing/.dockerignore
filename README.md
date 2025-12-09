# .dockerignore Templates

**Production-ready `.dockerignore` files for 87+ languages, frameworks, and tools.**

[![Website](https://img.shields.io/badge/Website-dockerignore.com-blue)](https://dockerignore.com)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Templates](https://img.shields.io/badge/Templates-87+-orange)](https://github.com/ronald2wing/.dockerignore)

Docker sends the entire build context to the daemon. A proper `.dockerignore` strips secrets, artifacts, caches, and editor files — making builds faster, leaner, and secure.

## Quick Start

```bash
# Framework template (self-contained, includes security)
curl -o .dockerignore https://raw.githubusercontent.com/ronald2wing/.dockerignore/master/frameworks/react.dockerignore

# Language template + security (language templates omit security patterns)
curl -o .dockerignore https://raw.githubusercontent.com/ronald2wing/.dockerignore/master/languages/python.dockerignore
curl -s https://raw.githubusercontent.com/ronald2wing/.dockerignore/master/common/security.dockerignore >> .dockerignore

# Interactive builder: https://dockerignore.com
```

## Categories

| Category  | Directory     | Description                                        |
| --------- | ------------- | -------------------------------------------------- |
| Framework | `frameworks/` | Self-contained. Security first. Use standalone.    |
| Language  | `languages/`  | Language patterns only. Combine with `common/`.    |
| Common    | `common/`     | Cross-cutting: security, cache, logs, git, Docker. |
| Tool      | `tools/`      | Build tools: webpack, vite, esbuild, etc.          |
| IDE       | `ides/`       | Editor configs: VS Code, IntelliJ, vim, etc.       |
| OS        | `os/`         | OS temp/system files: Linux, macOS, Windows.       |

## Combining Templates

```bash
# Language + common modules
cat languages/python.dockerignore common/security.dockerignore common/cache.dockerignore > .dockerignore

# Deduplicate when combining
cat languages/node.dockerignore common/security.dockerignore common/git.dockerignore | sort -u > .dockerignore

# Full stack: framework + OS + IDE (deduplicate with sort -u)
cat frameworks/nextjs.dockerignore os/linux.dockerignore ides/visual-studio-code.dockerignore | sort -u > .dockerignore
```

## Why This Matters

- **Security** — Including `.env` files in an image leaks credentials. Every framework template puts security first.
- **Build speed** — Excluding `node_modules/`, `target/`, and `.git/` shrinks the build context from hundreds of MB to kilobytes.
- **Cache efficiency** — Fewer files means fewer cache invalidations and faster rebuilds.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for the PR process and [TEMPLATE_STANDARDS.md](TEMPLATE_STANDARDS.md) for the specification every template must follow.

## Links

- **Website**: [dockerignore.com](https://dockerignore.com)
- **Repository**: [github.com/ronald2wing/.dockerignore](https://github.com/ronald2wing/.dockerignore)
- **Issues**: [GitHub Issues](https://github.com/ronald2wing/.dockerignore/issues)
- **License**: [MIT](LICENSE)
