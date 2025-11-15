# Documentation: utils/move-jsdoc.ts

## File Metadata

- **Path**: `utils/move-jsdoc.ts`
- **Size**: 1,994 bytes
- **Lines**: 61
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import fs from 'fs';


const REST_FOLDER = './ts/src/';
const WS_FOLDER = './ts/src/pro/';

function processFile(fileContent) {
    let fileSplit = fileContent.split('\n');

    const newFile: string[] = [];
    for (let i = 0; i < fileSplit.length; i++) {

        const currentLine = fileSplit[i];

        const isSignatureRegex = /\s*async\s\w+/;
        if (isSignatureRegex.test(currentLine)) {
            const nextLine = fileSplit[i + 1];
            const isJSDocRegex = /\s*\/\*\*/;
            if (isJSDocRegex.test(nextLine)) {
                let jsDocLines = [nextLine];
                let j = i + 2;
                while (fileSplit[j] && !/\s*\*\//.test(fileSplit[j])) {
                    jsDocLines.push(fileSplit[j]);
                    j++;
                }
                jsDocLines.push(fileSplit[j]);
                // remove 1 level of identation from jsdoc
                const spaces4 = '    ';
                const spaces5 = '     ';
                jsDocLines = jsDocLines.map((line, i) => (i == 0 ? spaces4 : spaces5) + line.trim());
                newFile.push(jsDocLines.join('\n'));
                newFile.push(currentLine);
                i = j;
            } else {
                newFile.push(currentLine);
            }
        } else {
            newFile.push(currentLine);
        }
    }

    const updatedContent = newFile.join('\n');
    return updatedContent;
}


function main() {

    const restFiles = fs.readdirSync(REST_FOLDER).filter(file => file.endsWith('.ts')).map(file => REST_FOLDER + file);
    const wsFiles = fs.readdirSync(WS_FOLDER).filter(file => file.endsWith('.ts')).map(file => WS_FOLDER + file);
    const allFiles = [...restFiles, ...wsFiles];

    for (const file of allFiles) {
        console.log(`Processing file: ${file}`);
        const fileContent = fs.readFileSync(file, 'utf8');
        const updatedContent = processFile(fileContent);
        fs.writeFileSync(file, updatedContent, 'utf8');
    }
}

main()
```

## High-Level Overview

This is a TypeScript file located at `utils/move-jsdoc.ts`.

**Functions defined**: main, processFile

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 48
- Comment lines: 1
- Blank lines: 12

### Main Components

**Functions** (2):
- `main()`
- `processFile()`

**Constants** (2):
- `REST_FOLDER`
- `WS_FOLDER`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `fs` (imported)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node utils/move-jsdoc.ts
```

