# Documentation: cli/package.json

## File Metadata

- **Path**: `cli/package.json`
- **Size**: 868 bytes
- **Lines**: 44
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
  "name": "ccxt-cli",
  "version": "1.0.0",
  "description": "CLI for the CCXT package",
  "main": "./js/cli.js",
  "type": "module",
  "scripts": {
    "build": "tsc",
    "publishPackage": "npm run build && npm publish"
  },
  "bin": {
    "ccxt": "js/cli.js"
  },
  "author": "CCXT",
  "license": "MIT",
  "keywords": [
    "ccxt",
    "cli",
    "crypto",
    "exchange",
    "trading"
  ],
  "dependencies": {
    "ansicolor": "^2.0.3",
    "as-table": "^1.0.55",
    "blessed": "^0.1.81",
    "ccxt": "^4.4.86",
    "clipboardy": "^4.0.0",
    "commander": "^14.0.0",
    "ololog": "^1.1.175",
    "open": "^10.1.2",
    "ora": "^8.2.0"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/ccxt/ccxt.git"
  },
  "readme": "README.md",
  "bugs": {
    "url": "https://github.com/ccxt/ccxt/issues"
  },
  "homepage": "https://ccxt.com"
}

```

## High-Level Overview

This is a JSON file located at `cli/package.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 43
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `js/cli.js` (referenced)
- `./js/cli.js` (referenced)
- `git+https://github.com/ccxt/ccxt.git` (referenced)
- `https://ccxt.com` (referenced)



## Testing & Execution

**To execute this JSON file:**

