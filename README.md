# actions-markdown-lint

A reusable GitHub Action for linting Markdown files in your repository. This action helps maintain consistent and high-quality documentation by checking your Markdown files against common style rules.

## Features

- Lints all Markdown files in your repository
- Configurable rules and settings
- Easy to integrate into your workflow
- Provides detailed feedback on linting issues

## Usage

### Basic Usage

```yaml
name: Markdown Lint

on:
  pull_request: {}

permissions:
  statuses: write
  checks: write
  contents: read
  pull-requests: read

jobs:
  markdown-lint:
    uses: cloudbuildlab/actions-markdown-lint/.github/workflows/markdown-lint.yml@v1
```

### Advanced Usage

```yaml
name: Markdown Lint

on:
  pull_request: {}

permissions:
  statuses: write
  checks: write
  contents: read
  pull-requests: read

jobs:
  markdown-lint:
    uses: cloudbuildlab/actions-markdown-lint/.github/workflows/markdown-lint.yml@v1
    with:
      config: |
        {
          "default": true,
          "whitespace": false,
          "line_length": false,
          "ul-start-left": false,
          "ul-indent": false,
          "no-inline-html": false,
          "no-bare-urls": false,
          "fenced-code-language": false,
          "first-line-h1": false,
          "no-duplicate-header": false,
          "no-emphasis-as-header": false,
          "single-h1": false
        }
      ignore: "node_modules custom-ignore-dir"
```

## Inputs

| Input | Description | Default |
|-------|-------------|---------|
| `config` | A markdownlint compatible JSON object string | See default config in workflow |
| `ignore` | Space-separated list of directories and files to ignore | `node_modules` |

## Default Configuration

The default configuration includes:

- Enables all default rules
- Disables specific rules that might be too strict:
  - `whitespace`
  - `line_length`
  - `ul-start-left`
  - `ul-indent`
  - `no-inline-html`
  - `no-bare-urls`
  - `fenced-code-language`
  - `first-line-h1`
  - `no-duplicate-header`
  - `no-emphasis-as-header`
  - `single-h1`

## Versioning

This workflow follows semantic versioning. You can use it in two ways:

1. **Major Version Tag** (Recommended):

   ```yaml
   uses: cloudbuildlab/actions-markdown-lint/.github/workflows/markdown-lint.yml@v1
   ```

   This will automatically use the latest release within the v1.x.x series.

2. **Specific Version**:

   ```yaml
   uses: cloudbuildlab/actions-markdown-lint/.github/workflows/markdown-lint.yml@v1.0.1
   ```

   This pins to a specific version for maximum stability.

### Version History

See the [Releases](../../releases) page for a full list of versions and changes.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
