# Documentation: wiki/examples/js/builtin-rate-limiting-rest-poller.md

## File Metadata

- **Path**: `wiki/examples/js/builtin-rate-limiting-rest-poller.md`
- **Size**: 657 bytes
- **Lines**: 30
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Builtin Rate Limiting Rest Poller](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';
import log from 'ololog';
import { nice as ansi } from 'ansicolor';
import asTable from 'as-table';

const exchange = new ccxt.coinbasepro ()
const repeat   = 100

async function test (symbol) {

    for (let i = 0; i < repeat; i++) {
        let ticker = await exchange.fetchTicker (symbol)
        log (exchange.id.green, exchange.iso8601 (exchange.milliseconds ()), ticker['datetime'], symbol.green, ticker['last'])
    }
}

const concurrent = [
    test ('BTC/USD'),
    test ('ETH/BTC'),
    test ('ETH/USD')
]

Promise.all (concurrent) 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/builtin-rate-limiting-rest-poller.md`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 21
- Comment lines: 0
- Blank lines: 9

### Main Components

**Functions** (1):
- `test()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `as-table` (imported)
- `ololog` (imported)
- `ansicolor` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

