# Documentation: wiki/examples/js/idex-fetch-balance.md

## File Metadata

- **Path**: `wiki/examples/js/idex-fetch-balance.md`
- **Size**: 388 bytes
- **Lines**: 19
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Idex Fetch Balance](./examples/js/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/idex-fetch-balance.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 14
- Comment lines: 0
- Blank lines: 5

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

**To execute this Markdown file:**

