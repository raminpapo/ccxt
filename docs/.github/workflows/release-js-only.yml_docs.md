# Documentation: .github/workflows/release-js-only.yml

## File Metadata

- **Path**: `.github/workflows/release-js-only.yml`
- **Size**: 1,140 bytes
- **Lines**: 44
- **Type**: YAML
- **Extension**: .yml


## Original Source Code

```yaml
name: Release JS workflow

on:
  workflow_dispatch:
    inputs:
      example_input:
        description: 'An example input value'
        required: false
        default: 'default-value'

permissions:
  contents: write


jobs:
  manual-job:
    runs-on: ubuntu-latest
    environment: Prod
    if: github.ref == 'refs/heads/master' && contains(fromJSON('["kroitor", "frosty00", "carlosmiei"]'), github.actor)

    steps:
      - name: Print Trigger Info
        run: |
          echo "This workflow was triggered manually."
          echo "Input value: ${{ github.event.inputs.example_input }}"
      - uses: actions/checkout@v4
        if: github.ref == 'refs/heads/master'
        with:
          token: ${{ secrets.GH_TOKEN }}
          fetch-depth: 2
          fetch-tags: true
      - uses: actions/checkout@v4
        if: github.ref != 'refs/heads/master'
        with:
          fetch-depth: 2
          fetch-tags: true
      - name: Install NPM dependencies
        run: npm ci
      - name: Transpile TS
        run: npm run tsBuild
      - uses: JS-DevTools/npm-publish@v3
        with:
          token: ${{ secrets.NPM_PROD }}

```

## High-Level Overview

This is a YAML file located at `.github/workflows/release-js-only.yml`.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 38
- Comment lines: 0
- Blank lines: 6

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this YAML file:**

