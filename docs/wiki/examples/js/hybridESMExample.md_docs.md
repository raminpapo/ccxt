# Documentation: wiki/examples/js/hybridESMExample.md

## File Metadata

- **Path**: `wiki/examples/js/hybridESMExample.md`
- **Size**: 559 bytes
- **Lines**: 24
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Hybridesmexample](./examples/js/)


 ```javascript
 import {version, huobi} from 'ccxt';

console.log('--------------------------------------------')
console.log('Yey importing ccxt as an ESM module!!!!!')
console.log('Version:', version)
console.log('--------------------------------------------')

const exchange = new huobi ({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET_KEY',
    'options': {
        'defaultType': 'swap',
    },
})

;(async () => {
    const result = await exchange.fetchBalance();
    console.log(result)
    }) () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/hybridESMExample.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 19
- Comment lines: 0
- Blank lines: 5

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `ccxt` (imported)



## Testing & Execution

**To execute this Markdown file:**

