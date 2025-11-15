# Documentation: cs/deploy.sh

## File Metadata

- **Path**: `cs/deploy.sh`
- **Size**: 291 bytes
- **Lines**: 11
- **Type**: Shell Script
- **Extension**: .sh


## Original Source Code

```bash
version=$(cat package.json | jq -r '.version')

bin_folder="./cs/ccxt/bin/Release/"

bin_file="ccxt.${version}.nupkg"

bin_path="${bin_folder}${bin_file}"

echo "Will publish nuget package: ${bin_path}"

dotnet nuget push ${bin_path} -k ${NUGGET_TOKEN} -s https://api.nuget.org/v3/index.json
```

## High-Level Overview

This is a Shell Script file located at `cs/deploy.sh`.



## Detailed Walkthrough

### Code Structure

- Total lines: 11
- Code lines: 6
- Comment lines: 0
- Blank lines: 5

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Shell Script file:**

```bash
bash cs/deploy.sh
```

