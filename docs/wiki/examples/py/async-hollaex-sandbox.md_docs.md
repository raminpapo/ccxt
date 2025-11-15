# Documentation: wiki/examples/py/async-hollaex-sandbox.md

## File Metadata

- **Path**: `wiki/examples/py/async-hollaex-sandbox.md`
- **Size**: 612 bytes
- **Lines**: 37
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Hollaex Sandbox](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from asyncio import run



async def test():
    import ccxt.async_support as ccxt

    print('CCXT Version', ccxt.__version__)

    # local sandbox keys
    exchange = ccxt.hollaex({
        'apiKey': "YOUR_SANDBOX_API_KEY",
        'secret': "YOUR_SANDBOX_SECRET",
    })

    exchange.set_sandbox_mode(True)

    markets = await exchange.load_markets()

    exchange.verbose = True

    balance = await exchange.fetch_balance()
    print(f"balance: {balance}")

    await exchange.close()


run(test()) 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-hollaex-sandbox.md`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 20
- Comment lines: 2
- Blank lines: 15

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

