# Documentation: wiki/examples/py/phemex-perpetual-balance.md

## File Metadata

- **Path**: `wiki/examples/py/phemex-perpetual-balance.md`
- **Size**: 792 bytes
- **Lines**: 34
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Phemex Perpetual Balance](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

from asyncio import run
import os
import sys
from pprint import pprint


import ccxt.async_support as ccxt  # noqa: E402

print('CCXT Version:', ccxt.__version__)

async def main():
    exchange = ccxt.phemex({
        "apiKey": "YOUR_API_KEY",
        "secret": "YOUR_SECRET",
        'options': { 'defaultType': 'swap' }
    })
    markets = await exchange.load_markets()
    # exchange.verbose = True  # uncomment for debugging purposes if necessary
    usd_balance = await exchange.fetch_balance({'code': 'USD'})
    btc_balance = await exchange.fetch_balance({'code': 'BTC'})
    balance = exchange.deep_extend(usd_balance, btc_balance)
    pprint(balance)
    await exchange.close()


run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/phemex-perpetual-balance.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 22
- Comment lines: 2
- Blank lines: 10

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

