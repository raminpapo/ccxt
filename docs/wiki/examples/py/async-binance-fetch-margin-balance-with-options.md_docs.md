# Documentation: wiki/examples/py/async-binance-fetch-margin-balance-with-options.md

## File Metadata

- **Path**: `wiki/examples/py/async-binance-fetch-margin-balance-with-options.md`
- **Size**: 774 bytes
- **Lines**: 39
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Binance Fetch Margin Balance With Options](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys
from pprint import pprint


import ccxt.async_support as ccxt  # noqa: E402


async def main():
    exchange = ccxt.binance({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        "options": {
            "fetchBalance": "margin",
        },
        # set verbose mode to True for debugging output
        # 'verbose': True,
    })
    while True:
        try:
            balance = await exchange.fetch_balance()
            pprint(balance)
        except Exception as e:
            print('fetch_balance() failed')
            print(e)
            break
    await exchange.close()


asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-binance-fetch-margin-balance-with-options.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 26
- Comment lines: 3
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

