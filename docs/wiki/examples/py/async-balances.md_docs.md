# Documentation: wiki/examples/py/async-balances.md

## File Metadata

- **Path**: `wiki/examples/py/async-balances.md`
- **Size**: 779 bytes
- **Lines**: 36
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Balances](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402


async def test(exchange):
    print(await exchange.fetch_balance())
    await exchange.close()


kraken = ccxt.kraken({
    'apiKey': "YOUR_API_KEY",
    'secret': "YOUR_SECRET",
    'verbose': True,  # switch it to False if you don't want the HTTP log
})
bitfinex = ccxt.bitfinex({
    'apiKey': "YOUR_API_KEY",
    'secret': "YOUR_SECRET",
    'verbose': True,  # switch it to False if you don't want the HTTP log
})

[asyncio.ensure_future(test(exchange)) for exchange in [kraken, bitfinex]]
pending = asyncio.Task.all_tasks()
loop = asyncio.get_event_loop()
loop.run_until_complete(asyncio.gather(*pending))
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-balances.md`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 24
- Comment lines: 1
- Blank lines: 11

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

