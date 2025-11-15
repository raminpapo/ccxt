# Documentation: wiki/examples/py/async-binance-fetch-margin-balance-with-params.md

## File Metadata

- **Path**: `wiki/examples/py/async-binance-fetch-margin-balance-with-params.md`
- **Size**: 638 bytes
- **Lines**: 34
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Binance Fetch Margin Balance With Params](./examples/py/)


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
    })
    while True:
        try:
            balance = await exchange.fetch_balance({'type': 'margin'})
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

This is a Markdown file located at `wiki/examples/py/async-binance-fetch-margin-balance-with-params.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 23
- Comment lines: 1
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

