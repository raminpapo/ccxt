# Documentation: examples/js/idex-fetch-balance.js

## File Metadata

- **Path**: `examples/js/idex-fetch-balance.js`
- **Size**: 326 bytes
- **Lines**: 14
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js';

const idex = ccxt.idex ({
    'apiKey': 'YOUR_IDEX_API_KEY',
    'secret': 'YOUR_IDEX_SECRET',
    'walletAddress': '0xYOUR_ETHEREUM_WALLET_ADDRESS',
    'privateKey': '0xYOUR_ETHEREUM_PRIVATE_KEY',
    'verbose': 0,
})

;(async () => {
    console.log (await idex.fetchBalance ())
}) ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/idex-fetch-balance.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 11
- Comment lines: 0
- Blank lines: 3

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/idex-fetch-balance.js
```

