# Documentation: ts/src/test/tests.init.ts

## File Metadata

- **Path**: `ts/src/test/tests.init.ts`
- **Size**: 775 bytes
- **Lines**: 29
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript


import { getCliArgValue, argvExchange, argvSymbol, argvMethod } from './tests.helpers.js';
import testMainClass from './tests.js';
import baseTestsInitRest from './base/tests.init.js';
import baseTestsInitWs from '../pro/test/base/tests.init.js';


// ########### args ###########
const isWs = getCliArgValue ('--ws');
const isBaseTests = getCliArgValue ('--baseTests');
const runAll = getCliArgValue ('--all');

// ####### base tests #######
if (isBaseTests) {
    if (isWs) {
        baseTestsInitWs ();
        console.log ('base WS tests passed!');
    } else {
        baseTestsInitRest ();
        console.log ('base REST tests passed!');
    }
    if (!runAll) {
        process.exit (0);
    }
}

(new testMainClass ()).init (argvExchange, argvSymbol, argvMethod);

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/tests.init.ts`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 20
- Comment lines: 2
- Blank lines: 7

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./base/tests.init.js` (imported)
- `./tests.js` (imported)
- `./tests.helpers.js` (imported)
- `../pro/test/base/tests.init.js` (imported)
- `./base/tests.init.js` (referenced)
- `./tests.js` (referenced)
- `./tests.helpers.js` (referenced)
- `../pro/test/base/tests.init.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/tests.init.ts
```

