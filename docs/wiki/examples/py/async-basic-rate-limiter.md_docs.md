# Documentation: wiki/examples/py/async-basic-rate-limiter.md

## File Metadata

- **Path**: `wiki/examples/py/async-basic-rate-limiter.md`
- **Size**: 419 bytes
- **Lines**: 25
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Basic Rate Limiter](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402


async def main():
    exchange = ccxt.binance()
    for i in range(0, 100):
        # this can be any call instead of fetch_ticker, really
        print(await exchange.fetch_ticker('ETH/BTC'))
    await exchange.close()


asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-basic-rate-limiter.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 13
- Comment lines: 2
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

