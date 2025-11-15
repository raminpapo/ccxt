# Documentation: wiki/examples/py/async-okx-margin-repay.md

## File Metadata

- **Path**: `wiki/examples/py/async-okx-margin-repay.md`
- **Size**: 1,005 bytes
- **Lines**: 44
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Okx Margin Repay](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys
from pprint import pprint


import ccxt.async_support as ccxt  # noqa: E402


async def main():
    exchange = ccxt.okx({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        # okx requires this: https://github.com/ccxt/ccxt/wiki/Manual#authentication
        'password': 'YOUR_API_PASSWORD',
        # 'verbose': True,  # for debug output
    })
    await exchange.load_markets()
    code = 'BTC'
    amount = 1
    order_id = 'YOUR_ORDER_ID_FROM_BORROWING'
    try:
        response = await exchange.repayCrossMargin(code, amount, {
            'ordId': order_id,
        })
        pprint(response)
    except ccxt.InsufficientFunds as e:
        print('repayCrossMargin() failed – not enough funds')
        print(e)
    except Exception as e:
        print('repayCrossMargin() failed')
        print(e)
    await exchange.close()


asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-okx-margin-repay.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 31
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

