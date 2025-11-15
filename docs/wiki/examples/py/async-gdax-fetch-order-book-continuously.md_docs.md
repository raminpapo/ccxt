# Documentation: wiki/examples/py/async-gdax-fetch-order-book-continuously.md

## File Metadata

- **Path**: `wiki/examples/py/async-gdax-fetch-order-book-continuously.md`
- **Size**: 705 bytes
- **Lines**: 28
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Gdax Fetch Order Book Continuously](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402


async def main(symbol):
    exchange = ccxt.binance()
    while True:
        print('--------------------------------------------------------------')
        print(exchange.iso8601(exchange.milliseconds()), 'fetching', symbol, 'ticker from', exchange.name)
        # this can be any call really
        ticker = await exchange.fetch_order_book(symbol)
        print(exchange.iso8601(exchange.milliseconds()), 'fetched', symbol, 'ticker from', exchange.name)
        print(ticker)


asyncio.run(main('BTC/USDT'))
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-gdax-fetch-order-book-continuously.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 16
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

