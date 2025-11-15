# Documentation: examples/js/hybridESMExample.js

## File Metadata

- **Path**: `examples/js/hybridESMExample.js`
- **Size**: 499 bytes
- **Lines**: 19
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

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

## High-Level Overview

This is a JavaScript file located at `examples/js/hybridESMExample.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 16
- Comment lines: 0
- Blank lines: 3

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `ccxt` (imported)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/hybridESMExample.js
```

