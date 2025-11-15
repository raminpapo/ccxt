# Documentation: wiki/examples/py/async-instantiate-all-at-once.md

## File Metadata

- **Path**: `wiki/examples/py/async-instantiate-all-at-once.md`
- **Size**: 607 bytes
- **Lines**: 29
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Instantiate All At Once](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
import asyncio


import ccxt.async_support as ccxt  # noqa: E402

exchanges = {}  # a placeholder for your instances


async def main():
    for id in ccxt.exchanges:
        exchange = getattr(ccxt, id)
        exchanges[id] = exchange()
    # now exchanges dictionary contains all exchange instances...
    print(await exchanges['bittrex'].fetch_order_book('ETH/BTC'))
    # close the aiohttp session object
    for id in exchanges:
        await exchanges[id].close()

asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-instantiate-all-at-once.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 16
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

