# Documentation: .git-templates/hooks/pre-push

## File Metadata

- **Path**: `.git-templates/hooks/pre-push`
- **Size**: 1,217 bytes
- **Lines**: 55
- **Type**: Unknown
- **Extension**: none


## Original Source Code

```
#!/bin/bash

# Check if changes are relevant
CHECK_DIRECTORIES="ts/ python/ccxt/ php/ build/"

MODIFIED_FILES=$(git diff --name-only upstream/master)
HAS_RELEVANT_CHANGES=false

for DIR in $CHECK_DIRECTORIES; do
    if echo "$MODIFIED_FILES" | grep -qE "^$DIR"; then
        HAS_RELEVANT_CHANGES=true
        break
    fi
done

if [ "$HAS_RELEVANT_CHANGES" = "false" ]; then
    echo "No relevant changes, skipping checks..."
    exit 0
fi

# Lint TS files
MODIFIED_TS_FILES=$(git diff --name-only upstream/master -- 'ts/**/*.ts')

ESLINT_EXIT_CODE=0
# Run eslint on the modified files
if [ "$MODIFIED_TS_FILES" != "" ]; then
    eslint $MODIFIED_TS_FILES
    ESLINT_EXIT_CODE=$?
fi

if [ $ESLINT_EXIT_CODE -ne 0 ]; then
    echo "ESLint failed, check the TypeScript files..."
    exit $ESLINT_EXIT_CODE
fi

# Run python linting
ruff ./python/ccxt
PYTHON_EXIT_CODE=$?

if [ $PYTHON_EXIT_CODE -ne 0 ]; then
    echo "Python linting failed, check the Python files..."
    exit $PYTHON_EXIT_CODE
fi

# Run PHP linting
npm run check-php-syntax
PHP_EXIT_CODE=$?

if [ $PHP_EXIT_CODE -ne 0 ]; then
    echo "PHP linting failed, check the PHP files..."
    exit $PHP_EXIT_CODE
fi

echo "All checks passed, pushing..."
exit 0
```

## High-Level Overview

This is a Unknown file located at `.git-templates/hooks/pre-push`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 37
- Comment lines: 6
- Blank lines: 12

### Main Components

**Constants** (7):
- `CHECK_DIRECTORIES`
- `ESLINT_EXIT_CODE`
- `HAS_RELEVANT_CHANGES`
- `MODIFIED_FILES`
- `MODIFIED_TS_FILES`
- `PHP_EXIT_CODE`
- `PYTHON_EXIT_CODE`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `ts/**/*.ts` (referenced)



## Testing & Execution

**To execute this Unknown file:**

