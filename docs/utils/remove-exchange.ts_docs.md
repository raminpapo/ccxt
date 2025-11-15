# Documentation: utils/remove-exchange.ts

## File Metadata

- **Path**: `utils/remove-exchange.ts`
- **Size**: 1,350 bytes
- **Lines**: 56
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import * as fs from 'fs';
import * as path from 'path';

function deleteFilesRecursively(directory: string, targetFileName: string): void {
    if (!fs.existsSync(directory)) {
        console.warn(`Directory not found: ${directory}`);
        return;
    }

    if (foldersToIgnore.some(folder => directory.endsWith(folder))) {
        return;
    }

    fs.readdirSync(directory).forEach(file => {
        const fullPath = path.join(directory, file);
        // console.log(`File: ${fullPath}`);

        if (fs.statSync(fullPath).isDirectory()) {
            deleteFilesRecursively(fullPath, targetFileName);
        } else if (file.startsWith(targetFileName)) {
            try {
                fs.unlinkSync(fullPath);
                console.log(`Deleted: ${fullPath}`);
            } catch (error) {
                console.error(`Failed to delete ${fullPath}:`, error);
            }
        }
    });
}

const foldersToIgnore = [
    '__pycache__',
]

const foldersToSearch = [
    './js',
    './ts',
    './python/ccxt',
    './cs',
    './php',
    './go'

];

const args = process.argv.slice(2);

if (args.length < 1) {
    console.error("Usage: tsx utils/remove-exchange.ts <targetFileName>");
    process.exit(1);
}

const targetFileName = args[0];


foldersToSearch.forEach(folder => deleteFilesRecursively(folder, targetFileName));

```

## High-Level Overview

This is a TypeScript file located at `utils/remove-exchange.ts`.

**Functions defined**: deleteFilesRecursively

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 42
- Comment lines: 1
- Blank lines: 13

### Main Components

**Functions** (1):
- `deleteFilesRecursively()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

- `path` (imported)
- `fs` (imported)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node utils/remove-exchange.ts
```

