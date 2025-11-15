# Documentation: wiki/examples/py/async-theocean-orderbook.md

## File Metadata

- **Path**: `wiki/examples/py/async-theocean-orderbook.md`
- **Size**: 582 bytes
- **Lines**: 33
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Theocean Orderbook](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys

if not sys.version >= '3.6':
    print('This script requires Python 3.6+')
    sys.exit()


import ccxt.async_support as ccxt  # noqa: E402


async def poll():
    exchange = ccxt.theocean()
    while True:
        yield await exchange.fetch_order_book('WETH/TUSD')
        await asyncio.sleep(exchange.rateLimit / 1000)


async def main():
    async for orderbook in poll():
        print(orderbook['bids'][0], orderbook['asks'][0])


asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-theocean-orderbook.md`.

**Functions defined**: main, poll

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 19
- Comment lines: 1
- Blank lines: 13

### Main Components

**Functions** (2):
- `main()`
- `poll()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

