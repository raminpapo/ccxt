# Documentation: ts/src/test/base/test.json.ts

## File Metadata

- **Path**: `ts/src/test/base/test.json.ts`
- **Size**: 1,062 bytes
- **Lines**: 42
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

// AUTO_TRANSPILE_ENABLED
// todo: per https://github.com/ttodua/ccxt/blob/17fc70fd7ccd8f6f5357e2dbd08aa30a1df0948b/ts/src/test/base/test.json.ts#L1

import assert from 'assert';
import ccxt, { BadRequest } from '../../../ccxt.js';

function testJson () {

    const exchange = new ccxt.Exchange ({
        'id': 'regirock',
    });

    // Test: object
    const obj = { "k": "v" };
    const objJson = exchange.json (obj);
    assert (objJson === "{\"k\":\"v\"}");

    // Test: list
    const list = [ 1, 2 ];
    const listJson = exchange.json (list);
    assert (listJson === "[1,2]");

    assert ('GO_SKIP_START');
    // Test: can serialize errors
    try {
        throw new BadRequest ("some error");
    } catch (e) {
        const errString = exchange.json (e);
        assert (errString === "{\"name\":\"BadRequest\"}");
    }
    assert ('GO_SKIP_END');

    // Test: json a string
    const str = "ccxt, rocks!";
    const serializedString = exchange.json (str);
    assert (serializedString === "\"ccxt, rocks!\"");

}

export default testJson;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/base/test.json.ts`.

**Functions defined**: testJson

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 25
- Comment lines: 6
- Blank lines: 11

### Main Components

**Functions** (1):
- `testJson()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../ccxt.js` (imported)
- `assert` (imported)
- `../../../ccxt.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/base/test.json.ts
```

