# AGENTS.md

## Repository Overview

Content-only repository. No build pipeline, test suite, linter, CI, or type checker.
Every file is a `.dockerignore` template or a Markdown document.
There is no `opencode.json` — this AGENTS.md is the sole instruction file.

## Category Rules (Critical — Agents Get These Wrong)

| Category  | Directory     | Label                | Key Rule                                                                         |
| --------- | ------------- | -------------------- | -------------------------------------------------------------------------------- |
| Framework | `frameworks/` | `FRAMEWORK TEMPLATE` | Security section MUST be first. Use standalone.                                  |
| Language  | `languages/`  | `LANGUAGE TEMPLATE`  | MUST NOT include security patterns. Combine with `common/security.dockerignore`. |
| Common    | `common/`     | `COMMON TEMPLATE`    | Cross-cutting: security, cache, logs, git, Docker, backup, testing.              |
| Tool      | `tools/`      | `TOOL TEMPLATE`      | Build/deploy tool patterns. Combine as needed.                                   |
| IDE       | `ides/`       | `IDE TEMPLATE`       | Editor config files. Combine as needed.                                          |
| OS        | `os/`         | `OS TEMPLATE`        | OS-specific temp/system files. Combine as needed.                                |

The label appears in **two places**: the `# LABEL for Name` header line and the `• TEMPLATE TYPE:` metadata field.

## File Naming

Lowercase, hyphens for spaces. Strip dots and special characters. Use the GitHub repo name for JS frameworks.

| Official Name      | Correct              | WRONG          |
| ------------------ | -------------------- | -------------- |
| Next.js            | `nextjs`             | `next.js`      |
| Express.js         | `express`            | `express.js`   |
| .NET               | `dotnet`             | `.net`         |
| C#                 | `csharp`             | `c#`           |
| React Native       | `react-native`       | `react_native` |
| Visual Studio Code | `visual-studio-code` | `vscode`       |

Full rules: [TEMPLATE_STANDARDS.md §6](TEMPLATE_STANDARDS.md#6-naming-conventions).

## Creating a Template

**Always copy an existing template from the same directory** — never invent a new format.

Full specification: [TEMPLATE_STANDARDS.md](TEMPLATE_STANDARDS.md). Key rules:

- **Header**: `#` + 78 `=` (80 chars total). Must include `Created by`, label, website, repository.
- **Metadata block**: `#` + 78 `━` (80 chars total). Must include `TEMPLATE TYPE` and `PURPOSE`.
- **Sections**: `#` + 84 `•` (86 chars total). Framework section order is fixed:
  1. Security & Sensitive Data
  2. Build Artifacts & Distribution
  3. Dependency Management & Package Cache
  4. Development & Runtime Artifacts
  5. Testing & Quality Assurance
  6. Documentation & Examples
  7. Tool-Specific Patterns
  8. IDE / Editor Files
     (Other categories: follow existing templates in the same directory.)
- **Pattern order within sections**: `**/` first, then `.` prefixed, then plain text.
- One pattern per line, no trailing whitespace, no duplicate patterns.

## Combining Templates

Always deduplicate with `sort -u` — templates share many patterns:

```bash
cat languages/python.dockerignore common/security.dockerignore common/cache.dockerignore | sort -u > .dockerignore
```

## Validation

```bash
# Check for duplicate patterns
sort template.dockerignore | uniq -d

# Count non-comment lines
grep -c '^[^#]' template.dockerignore
```

## References

- [TEMPLATE_STANDARDS.md](TEMPLATE_STANDARDS.md) — full format, naming, and QA specification
- [CONTRIBUTING.md](CONTRIBUTING.md) — PR process and review criteria
- [README.md](README.md) — project overview and usage examples
