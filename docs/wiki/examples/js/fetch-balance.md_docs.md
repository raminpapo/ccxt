# Documentation: wiki/examples/js/fetch-balance.md

## File Metadata

- **Path**: `wiki/examples/js/fetch-balance.md`
- **Size**: 780 bytes
- **Lines**: 33
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Balance](./examples/js/)


 ```javascript
 "use strict";

const ccxt      = require ('../../ccxt.js');

// instantiate the exchange
let exchange = new ccxt.coinbasepro  ({
    'apiKey': 'XXXXXXXXXXXXXX',
    'secret': 'YYYYYYYYYYYYYY',
    'password': 'ZZZZZZ', // if exchange requires password
});


async function checkMyBalance() {
    try {
        // fetch account balance from the exchange
        let myBalance = await exchange.fetchBalance ();

        // output the result
        console.log (exchange.id, 'fetched balance', myBalance);

    } catch (e) {
        // fpr advanced error-handling, see the "advanced-error-handling.js" example file
        console.log ('[' + e.constructor.name + '] ' + e.message);
        throw e;
    }
}

checkMyBalance(); 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/fetch-balance.md`.

**Functions defined**: checkMyBalance



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 20
- Comment lines: 4
- Blank lines: 9

### Main Components

**Functions** (1):
- `checkMyBalance()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

