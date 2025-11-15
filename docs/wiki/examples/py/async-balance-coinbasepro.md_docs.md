# Documentation: wiki/examples/py/async-balance-coinbasepro.md

## File Metadata

- **Path**: `wiki/examples/py/async-balance-coinbasepro.md`
- **Size**: 554 bytes
- **Lines**: 29
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Balance Coinbasepro](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402


async def test():
    exchange = ccxt.coinbasepro({
        'apiKey': "YOUR_API_KEY",
        'secret': "YOUR_SECRET",
        'password': "YOUR_PASSWORD",
        'verbose': True,  # switch it to False if you don't want the HTTP log
    })
    # move to sandbox
    exchange.urls['api'] = exchange.urls['test']
    print(await exchange.fetch_balance())


asyncio.run(test())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-balance-coinbasepro.md`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 17
- Comment lines: 2
- Blank lines: 10

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

