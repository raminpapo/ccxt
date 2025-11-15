# Documentation: utils/package-test.sh

## File Metadata

- **Path**: `utils/package-test.sh`
- **Size**: 485 bytes
- **Lines**: 20
- **Type**: Shell Script
- **Extension**: .sh


## Original Source Code

```bash
#!/bin/bash

# Asserts the npm package works as expected, using ESM and CJS.
npm pack . --silent
mv ccxt-*.tgz ./utils/package-test/
cd ./utils/package-test
npm install ccxt-*.tgz
node test-esm.mjs
return_code=$?
node test-cjs.cjs
cjs_return_code=$?
rm -rf node_modules ccxt-*.tgz package-lock.json package.json
npm init -y > /dev/null
if [ $return_code -eq 0 ] && [ $cjs_return_code -eq 0 ]; then
  echo "Package test successful"
  exit 0
else
  echo "Package test failed"
  exit 1
fi
```

## High-Level Overview

This is a Shell Script file located at `utils/package-test.sh`.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 17
- Comment lines: 2
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
