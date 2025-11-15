# Documentation: utils/init_actions.sh

## File Metadata

- **Path**: `utils/init_actions.sh`
- **Size**: 593 bytes
- **Lines**: 22
- **Type**: Shell Script
- **Extension**: .sh


## Original Source Code

```bash
#!/bin/bash
OUTPUT=$(./utils/check_modified_files.sh | tr -d '\n')
# echo "1"
IMPORTANT_MODIFIED=$(echo "$OUTPUT" | jq -r '.important_modified')
# echo "2"
REST_FILES=$(echo "$OUTPUT" | jq -r '.rest_exchanges | join(" ")')
WS_FILES=$(echo "$OUTPUT" | jq -r '.ws_exchanges | join(" ")')
# echo "4"
echo "important_modified=$IMPORTANT_MODIFIED" >> $GITHUB_ENV
# echo "5"
echo "rest_files=$REST_FILES" >> $GITHUB_ENV
# echo "6"
echo "ws_files=$WS_FILES" >> $GITHUB_ENV
# echo "7"

FILE_NAME="shared_env.txt"

{
  echo "$IMPORTANT_MODIFIED"
  echo "$REST_FILES"
  echo "$WS_FILES"
} > "$FILE_NAME"
```

## High-Level Overview

This is a Shell Script file located at `utils/init_actions.sh`.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 13
- Comment lines: 7
- Blank lines: 2

### Main Components

**Constants** (5):
- `FILE_NAME`
- `IMPORTANT_MODIFIED`
- `OUTPUT`
- `REST_FILES`
- `WS_FILES`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Shell Script file:**

```bash
bash utils/init_actions.sh
```

