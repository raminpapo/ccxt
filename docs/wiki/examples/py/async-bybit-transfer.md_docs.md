# Documentation: wiki/examples/py/async-bybit-transfer.md

## File Metadata

- **Path**: `wiki/examples/py/async-bybit-transfer.md`
- **Size**: 1,020 bytes
- **Lines**: 36
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Bybit Transfer](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys
from pprint import pprint


import ccxt.async_support as ccxt  # noqa: E402


async def main():
    exchange = ccxt.bybit({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        # 'verbose': True,  # for debug output
    })
    await exchange.load_markets()
    try:
        pprint(await exchange.fetch_transfers())  # Fetch your transfer history
        # pprint(await exchange.transfer('USDT', 1.0, 'swap', 'spot'))  # Transfer to the spot wallet
        # pprint(await exchange.transfer('USDT', 1.0, 'spot', 'future'))  # Transfer to the Derivatives wallet
        # pprint(await exchange.transfer('USDT', 1.0, 'spot', 'swap'))  # Transfer to the Derivatives wallet
        # pprint(await exchange.transfer('USDC', 1.0, 'spot', 'option'))  # Transfer to the USDC Derivatives wallet
    except Exception as e:
        print(e)
    await exchange.close()


asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-bybit-transfer.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 20
- Comment lines: 6
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

