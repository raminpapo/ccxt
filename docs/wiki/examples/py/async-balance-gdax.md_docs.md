# Documentation: wiki/examples/py/async-balance-gdax.md

## File Metadata

- **Path**: `wiki/examples/py/async-balance-gdax.md`
- **Size**: 549 bytes
- **Lines**: 29
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Balance Gdax](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402


async def test():
    gdax = ccxt.gdax({
        'apiKey': "YOUR_API_KEY",
        'secret': "YOUR_SECRET",
        'password': "YOUR_PASSWORD",
        'verbose': True,  # switch it to False if you don't want the HTTP log
    })
    # move gdax to sandbox
    gdax.urls['api'] = 'https://api-public.sandbox.gdax.com'
    print(await gdax.fetch_balance())


asyncio.run(test())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-balance-gdax.md`.

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

- `https://api-public.sandbox.gdax.com` (referenced)



## Testing & Execution

**To execute this Markdown file:**

