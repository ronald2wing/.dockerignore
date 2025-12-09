# Template Standards

Canonical specification for all `.dockerignore` templates in this repository.

---

## 1. Template Categories

Templates are organized by category. Each category has a directory and set of rules:

| Category  | Directory     | Rules                                                                           |
| --------- | ------------- | ------------------------------------------------------------------------------- |
| Framework | `frameworks/` | Self-contained. Security section **first**. Use standalone.                     |
| Language  | `languages/`  | Language-specific patterns only. No security. Combine with `common/`.           |
| Common    | `common/`     | Cross-cutting concerns (security, cache, logs, git, Docker). Combine as needed. |
| Tool      | `tools/`      | Build and deploy tool patterns. Combine as needed.                              |
| IDE       | `ides/`       | Editor config files. Combine as needed.                                         |
| OS        | `os/`         | OS-specific temp/system files. Combine as needed.                               |

## 2. Template Type Labels

Every template declares its type in two places: the `#` header line and the metadata block. Use the short label form:

| Category  | Label                |
| --------- | -------------------- |
| Framework | `FRAMEWORK TEMPLATE` |
| Language  | `LANGUAGE TEMPLATE`  |
| Common    | `COMMON TEMPLATE`    |
| Tool      | `TOOL TEMPLATE`      |
| IDE       | `IDE TEMPLATE`       |
| OS        | `OS TEMPLATE`        |

## 3. Template Structure

### 3.1 Header

Every template opens with a header using `=` separators (80 characters wide):

```dockerignore
# ==============================================================================
# Created by https://dockerignore.com/
# FRAMEWORK TEMPLATE for React
# Website: https://reactjs.org/
# Repository: https://github.com/facebook/react
# ==============================================================================
```

### 3.2 Metadata

After the header, a metadata block with box-drawing `━` separators (80 characters wide):

```dockerignore
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
# TEMPLATE OVERVIEW & USAGE NOTES
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
# • TEMPLATE TYPE: FRAMEWORK TEMPLATE
# • PURPOSE: React-specific ignore patterns
# • OFFICIAL SOURCES: React community patterns and best practices
# • DESIGN PHILOSOPHY: Self-contained template with security patterns first
```

Required fields: `TEMPLATE TYPE`, `PURPOSE`. Common additional fields: `OFFICIAL SOURCES`, `DESIGN PHILOSOPHY`, `COMBINATION GUIDANCE`, `SECURITY CONSIDERATIONS`, `BEST PRACTICES`.

### 3.3 Body

Sections are separated by 78 bullet dots (`•`) (80 characters wide):

```dockerignore
# ••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••
# SECTION TITLE
# ••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••••
# Optional description

.gitignore
node_modules/
```

### 3.4 Section Order (Frameworks)

Framework templates must use this exact section order:

1. **Security & Sensitive Data**
2. **Build Artifacts & Distribution**
3. **Dependency Management & Package Cache**
4. **Development & Runtime Artifacts**
5. **Testing & Quality Assurance**
6. **Documentation & Examples**
7. **Tool-Specific Patterns**
8. **IDE / Editor Files**

Other categories have no fixed section order. Follow the conventions of existing templates in the same directory.

## 4. Pattern Guidelines

### Grouping

Patterns are grouped by prefix type in this order:

1. **`\*\*/` patterns** — recursive directory matches
2. **`.` prefixed patterns** — dotfiles and dot-directories
3. **Plain text patterns** — names without a leading dot

Within each group, follow the sorting conventions of existing templates.

### Formatting

- One pattern per line.
- No duplicate patterns anywhere in the file.
- Comments occupy their own line, directly above the patterns they describe.
- No trailing whitespace.

## 5. Security Requirements

### Framework Templates

Must include a security section as the **first body section**. Baseline patterns:

```dockerignore
.env
.env.*
```

Common additions: `*.pem`, `*.key`, `credentials.json`, `secrets.yml`, and framework-specific credential files.

### Language Templates

Must **not** include security patterns. Users combine with `common/security.dockerignore`.

## 6. Naming Conventions

| Rule                     | Example                             |
| ------------------------ | ----------------------------------- |
| Lowercase only           | `python`, `react`                   |
| Hyphens for spaces       | `react-native`, `spring-boot`       |
| Strip dots               | `nextjs` (not `next.js`), `dotnet`  |
| Strip special characters | `csharp` (not `C#`)                 |
| Use GitHub repo name     | `express` (not `express.js`), `vue` |
| Full name for languages  | `javascript`, `typescript`          |

| Official Name      | File Name                         |
| ------------------ | --------------------------------- |
| Next.js            | `nextjs.dockerignore`             |
| Express.js         | `express.dockerignore`            |
| Visual Studio Code | `visual-studio-code.dockerignore` |
| .NET               | `dotnet.dockerignore`             |
| C#                 | `csharp.dockerignore`             |
| React Native       | `react-native.dockerignore`       |
| Spring Boot        | `spring-boot.dockerignore`        |
| Python             | `python.dockerignore`             |

## 7. Validation & Testing

### Pattern Checks

```bash
# Check for duplicate patterns
sort template.dockerignore | uniq -d

# Count non-comment lines
grep -c '^[^#]' template.dockerignore
```

### Build Test

```bash
rm -rf /tmp/dockerignore-test && mkdir /tmp/dockerignore-test && cd /tmp/dockerignore-test
cp ../path/to/template.dockerignore .dockerignore
echo 'FROM alpine:latest' > Dockerfile
touch .env .env.local test.log
mkdir -p node_modules build dist .vscode .git
docker build --no-cache .
```

### Validation Checklist

- [ ] File name follows naming conventions (Section 6)
- [ ] File placed in the correct category directory (Section 1)
- [ ] Header and metadata block match the standard format (Section 3.1–3.2)
- [ ] Short template type label used, in both header and metadata block (Section 2)
- [ ] Header: `===` (80 chars). Metadata: `━` (80 chars). Sections: `•••` (80 chars)
- [ ] Framework template: security section is first; Language template: no security section (Section 5)
- [ ] Patterns grouped by prefix: `**/`, `.`, plain text (Section 4)
- [ ] No duplicate patterns
- [ ] Docker build succeeds with the template
- [ ] One pattern per line, no trailing whitespace

---

Maintained by [dockerignore.com](https://dockerignore.com)
