# Documentation: .github/ISSUE_TEMPLATE/FEATURE_REQUEST.yml

## File Metadata

- **Path**: `.github/ISSUE_TEMPLATE/FEATURE_REQUEST.yml`
- **Size**: 1,360 bytes
- **Lines**: 39
- **Type**: YAML
- **Extension**: .yml


## Original Source Code

```yaml
name: Feature Request
description: Suggest an idea to help improve CCXT
labels: ["enhancement"]
body:
  - type: markdown
    attributes:
      value: |
        ## Thank you for creating a new feature request report!

        If you feel that you would be useful in implementing the feature yourself, please read our [contributing guidelines](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md)

  - type: checkboxes
    attributes:
      label: Preliminary Checks
      options:
        - label: "I have already searched for [existing issues](https://github.com/ccxt/ccxt/issues) and confirmed that this issue is not a duplicate"
          required: true

  - type: textarea
    attributes:
      label: Is your feature request related to a problem? Please describe
      description: A clear and concise description of what the problem is. Ex. I'm always frustrated when [...]
    validations:
      required: false

  - type: textarea
    attributes:
      label: Describe the solution you'd like
      description: A clear and concise description of what you want to happen.
    validations:
      required: true

  - type: textarea
    attributes:
      label: Describe alternatives you've considered
      description: A clear and concise description of any alternative solutions or features you've considered
    validations:
      required: false

```

## High-Level Overview

This is a YAML file located at `.github/ISSUE_TEMPLATE/FEATURE_REQUEST.yml`.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 32
- Comment lines: 1
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

