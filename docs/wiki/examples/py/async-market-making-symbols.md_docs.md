# Documentation: wiki/examples/py/async-market-making-symbols.md

## File Metadata

- **Path**: `wiki/examples/py/async-market-making-symbols.md`
- **Size**: 1,083 bytes
- **Lines**: 43
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Market Making Symbols](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

from asyncio import gather, run
from pprint import pprint
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402


async def load_markets(exchange):
    results = None
    try:
        await exchange.load_markets()
        print('Loaded', len(exchange.symbols), exchange.id, 'symbols')
        results = []
        for market in exchange.markets.values():
            if market['maker'] <= 0:
                results.append({'exchange': exchange.id, 'symbol': market['symbol']})
        if len(results) < 1:
            results = None
    except:
        results = None
    await exchange.close()
    return results


async def main():
    exchanges = [getattr(ccxt, exchange_id)() for exchange_id in ccxt.exchanges]
    # exchanges = [exchange for exchange in exchanges if exchange.certified]
    results = await gather(*[load_markets(exchange) for exchange in exchanges])
    results = [result for result in results if result is not None]
    pprint(results)


run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-market-making-symbols.md`.

**Functions defined**: main, load_markets

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 29
- Comment lines: 2
- Blank lines: 12

### Main Components

**Functions** (2):
- `load_markets()`
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

