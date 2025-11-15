# Documentation: wiki/examples/py/async-basic-orderbook.md

## File Metadata

- **Path**: `wiki/examples/py/async-basic-orderbook.md`
- **Size**: 628 bytes
- **Lines**: 33
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Basic Orderbook](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402


async def test():

    exchange = ccxt.okex({
        # 'proxy': 'https://cors-anywhere.herokuapp.com/',
        # 'origin': 'foobar',  # when using CORS proxies, set this to some random string
    })

    try:
        orderbook = await exchange.fetch_order_book('BTC/USDT')
        await exchange.close()
        return orderbook
    except ccxt.BaseError as e:
        print(type(e).__name__, str(e), str(e.args))
        raise e


asyncio.run(test())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-basic-orderbook.md`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 18
- Comment lines: 3
- Blank lines: 12

### Main Components

**Functions** (1):
- `test()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

