# Documentation: wiki/examples/js/fetch-funding-rate-history.md

## File Metadata

- **Path**: `wiki/examples/js/fetch-funding-rate-history.md`
- **Size**: 700 bytes
- **Lines**: 31
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Funding Rate History](./examples/js/)


 ```javascript
 import ccxt from '../../js/ccxt.js';
import asTable from 'as-table';

const table  = asTable.configure ({ delimiter: ' | ' });

console.log ('CCXT Version:', ccxt.version)

async function main () {

    const exchange = new ccxt.binanceusdm()
        , symbol = 'ETH/USDT'
        , since = undefined
        , limit = undefined
        , params = {}

    // ------------------------------------------------------------------------
    // fetch the history of the funding rate for a symbol

    const response = await exchange.fetchFundingRateHistory (symbol, since, limit, params)

    console.log (table (response))

}

main ()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/fetch-funding-rate-history.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 17
- Comment lines: 2
- Blank lines: 12

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `as-table` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

