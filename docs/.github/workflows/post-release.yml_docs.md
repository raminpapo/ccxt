# Documentation: .github/workflows/post-release.yml

## File Metadata

- **Path**: `.github/workflows/post-release.yml`
- **Size**: 769 bytes
- **Lines**: 27
- **Type**: YAML
- **Extension**: .yml


## Original Source Code

```yaml
name: On release published (pushback changelog)

on:
  workflow_run:
    workflows: ["Release workflow"]
    types:
      - completed
jobs:
  changelog:
    if: ${{ github.event.workflow_run.conclusion == 'success' }}
    name: Update changelog
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          token: ${{ secrets.GH_TOKEN }}
          fetch-depth: 2
      - uses: rhysd/changelog-from-release/action@v3
        with:
          file: CHANGELOG.md
          github_token: ${{ secrets.GH_TOKEN }}
  failed-release:
    if: ${{ github.event.workflow_run.conclusion != 'success' }}
    runs-on: ubuntu-latest
    steps:
      - name: Skip changelog update
        run: echo "Won't continue because the Release workflow failed."
```

## High-Level Overview

This is a YAML file located at `.github/workflows/post-release.yml`.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 26
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this YAML file:**

