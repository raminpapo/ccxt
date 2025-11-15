# Documentation: wiki/examples/py/async-generator-basic.md

## File Metadata

- **Path**: `wiki/examples/py/async-generator-basic.md`
- **Size**: 388 bytes
- **Lines**: 28
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Generator Basic](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402


async def poll():
    exchange = ccxt.poloniex()
    while True:
        yield await exchange.fetch_ticker('ETH/BTC')


async def main():
    async for ticker in poll():
        print(ticker)


asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-generator-basic.md`.

**Functions defined**: main, poll

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 15
- Comment lines: 1
- Blank lines: 12

### Main Components

**Functions** (2):
- `main()`
- `poll()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

