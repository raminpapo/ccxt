# Documentation: wiki/examples/ts/compare-two-exchanges-capabilities.md

## File Metadata

- **Path**: `wiki/examples/ts/compare-two-exchanges-capabilities.md`
- **Size**: 1,644 bytes
- **Lines**: 42
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Compare Two Exchanges Capabilities](./examples/ts/)


 ```javascript
 import ccxt from '../../js/ccxt.js';

// AUTO-TRANSPILE //

async function example () {
    const prefix = '-';
    const exchange_1 = new ccxt.okx ();
    const exchange_2 = new ccxt.htx ();
    const keys_1 = Object.keys (exchange_1.has);
    const keys_2 = Object.keys (exchange_2.has);
    // check missing from exchange-1
    console.log ('### checking missing functionalities from exchange-1:', exchange_1.id);
    for (let i = 0; i < keys_2.length; i++) {
        const key = keys_2[i];
        if (exchange_2.has[key]) {
            if (!keys_1.includes (key)) {
                console.log (prefix, key, 'does not exist in', exchange_1.id, 'as opposed to', exchange_2.id);
            } else if (exchange_2.has[key] !== exchange_1.has[key]) {
                console.log (prefix, key, '> ', exchange_1.id, ':', exchange_1.has[key], ',', exchange_2.id, ':', exchange_2.has[key]);
            }
        }
    }
    // check missing from exchange-2
    console.log ('### checking missing functionalities from exchange-2:', exchange_2.id);
    for (let i = 0; i < keys_1.length; i++) {
        const key = keys_1[i];
        if (exchange_1.has[key]) {
            if (!keys_2.includes (key)) {
                console.log (prefix, key, 'does not exist in', exchange_2.id, 'as opposed to', exchange_1.id);
            } else if (exchange_1.has[key] !== exchange_2.has[key]) {
                console.log (prefix, key, '> ', exchange_2.id, ':', exchange_2.has[key], ',', exchange_1.id, ':', exchange_1.has[key]);
            }
        }
    }
}
await example ();
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/ts/compare-two-exchanges-capabilities.md`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 34
- Comment lines: 3
- Blank lines: 5

### Main Components

**Functions** (1):
- `example()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

