# Contributing

## Getting Started

```bash
git clone https://github.com/ronald2wing/.dockerignore.git
cd .dockerignore
git checkout -b feature/new-template-name
```

## Creating a Template

1. **Choose the correct directory**: `frameworks/`, `languages/`, `common/`, `tools/`, `ides/`, or `os/`.
2. **Copy an existing template** from that same directory — do not invent a new format.
3. **Follow [TEMPLATE_STANDARDS.md](TEMPLATE_STANDARDS.md)** exactly for structure, naming, labels, and section order.
4. **Category-specific rules**:
   - **Framework templates**: Security section must be first.
   - **Language templates**: Must NOT include security patterns. Users add `common/security.dockerignore`.

### Format Rules

All formatting, naming, and structural rules are specified in [TEMPLATE_STANDARDS.md](TEMPLATE_STANDARDS.md).

## Testing Your Template

```bash
# Create a test project
rm -rf /tmp/test-dockerignore && mkdir /tmp/test-dockerignore && cd /tmp/test-dockerignore
echo 'FROM alpine:latest' > Dockerfile

# Copy your template and create test files
cp ../path/to/your-template.dockerignore .dockerignore
touch .env .env.local test.log debug.log
mkdir -p node_modules build dist .vscode

# Test the build
docker build --no-cache .
```

## Submitting a Pull Request

- One template or fix per pull request.
- Use a clear, specific title: `Add template for [Name]` or `Fix [description]`.
- Include:
  - What the template covers (and what it deliberately omits)
  - Build output showing the template works
  - Duplicate pattern check results
  - References to official docs or community patterns
- Respond to reviewer feedback.

## Review Criteria

1. Correct directory, file name, and structure per [TEMPLATE_STANDARDS.md](TEMPLATE_STANDARDS.md)
2. Pattern accuracy — no missing common files, no false exclusions
3. Security section present and first (frameworks only)
4. No duplicate patterns
5. Clean, concise comments

## Community

- **Issues**: [GitHub Issues](https://github.com/ronald2wing/.dockerignore/issues)
- **Discussions**: [GitHub Discussions](https://github.com/ronald2wing/.dockerignore/discussions)

Be respectful, constructive, and inclusive.
