# Documentation: .github/ISSUE_TEMPLATE/BUG_REPORT.yml

## File Metadata

- **Path**: `.github/ISSUE_TEMPLATE/BUG_REPORT.yml`
- **Size**: 1,639 bytes
- **Lines**: 58
- **Type**: YAML
- **Extension**: .yml


## Original Source Code

```yaml
name: New Issue
description: Report bugs here
labels: []
assignees: []
body:
  - type: markdown
    attributes:
      value: |
        ## Ensure :
        - You have already searched across the existing issues
        - Your local CCXT version is up to date (check the [latest available version](https://github.com/ccxt/ccxt/blob/master/package.json#L3) )
        - Read the [FAQ](https://github.com/ccxt/ccxt/wiki/FAQ) or search for the specific subject in the [Manual](https://github.com/ccxt/ccxt/wiki/Manual) (eg: `Exchange Properties`, `Rate Limit`, `Authentication`, `API keys`, etc).
        - Read the [Troubleshooting](https://github.com/ccxt/ccxt/wiki/Manual#troubleshooting) to better understand your issue.

        ## Please:
        - Set `exchange.verbose = true` property before calling exchange functions
        - Provide the minimal, reproducible example/code
        - Surround your code/output with triple backticks:
          ````markdown
          ```
          your data here
          ```
        - Hide the keys & credentials.

  - type: input
    id: operating-system
    attributes:
      label: Operating System
    validations:
      required: false

  - type: dropdown
    id: language
    attributes:
      multiple: true
      label: Programming Language
      options:
        - JavaScript
        - Python
        - PHP
        - C#
        - GO
    validations:
      required: false

  - type: input
    id: ccxt-version
    attributes:
      label: CCXT Version
    validations:
      required: false

  - type: textarea
    attributes:
      label: Description
    validations:
      required: false

```

## High-Level Overview

This is a YAML file located at `.github/ISSUE_TEMPLATE/BUG_REPORT.yml`.



## Detailed Walkthrough

### Code Structure

- Total lines: 58
- Code lines: 50
- Comment lines: 2
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

