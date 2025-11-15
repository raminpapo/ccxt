# Documentation: .github/ISSUE_TEMPLATE/NEW_EXCHANGE.yml

## File Metadata

- **Path**: `.github/ISSUE_TEMPLATE/NEW_EXCHANGE.yml`
- **Size**: 992 bytes
- **Lines**: 34
- **Type**: YAML
- **Extension**: .yml


## Original Source Code

```yaml
name: New Exchange Request
description: Request the implementation of an exchange not yet implemented in the CCXT library
labels: ["new exchange"]
body:
  - type: input
    id: exchange-name
    attributes:
      label: Exchange Name
    validations:
      required: true

  - type: input
    id: exchange-url
    attributes:
      label: URL of the Exchange
      placeholder: https://www.binance.com
    validations:
      required: true

  - type: input
    id: api-docs
    attributes:
      label: URL of the Exchange's API docs
      placeholder: https://binance-docs.github.io/apidocs
    validations:
      required: true

  - type: textarea
    attributes:
      label: Why should this exchange be implemented?
      description: We would love to add this exchange to CCXT. There are a lot of other exchanges that we would also love to add to CCXT. Why should resources be devoted to adding this exchange to CCXT before adding other exchanges?
    validations:
      required: false

```

## High-Level Overview

This is a YAML file located at `.github/ISSUE_TEMPLATE/NEW_EXCHANGE.yml`.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 30
- Comment lines: 0
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this YAML file:**

