# Documentation: wiki/examples/py/async-binance-margin-repay.md

## File Metadata

- **Path**: `wiki/examples/py/async-binance-margin-repay.md`
- **Size**: 827 bytes
- **Lines**: 40
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Binance Margin Repay](./examples/py/)


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
        'verbose': True,  # for debug output
    })
    await exchange.load_markets()
    code = 'BTC'
    amount = 1
    currency = exchange.currency(code)
    try:
        response = await exchange.sapi_post_margin_repay({
            'asset': currency['id'],
            'amount': exchange.currency_to_precision(code, amount)
        })
        pprint(response)
    except Exception as e:
        print('sapi_post_margin_repay() failed')
        print(e)
    await exchange.close()


asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-binance-margin-repay.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 29
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

