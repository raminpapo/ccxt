# Documentation: wiki/examples/py/async-ticker.md

## File Metadata

- **Path**: `wiki/examples/py/async-ticker.md`
- **Size**: 461 bytes
- **Lines**: 28
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Ticker](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys
from pprint import pprint


import ccxt.async_support as ccxt  # noqa: E402


async def test(id, symbol):
    exchange = getattr(ccxt, id)()
    ticker = await exchange.fetch_ticker(symbol)
    await exchange.close()
    return ticker


if __name__ == '__main__':
    id = 'binance'
    symbol = 'ETH/BTC'
    pprint(asyncio.run(test(id, symbol)))
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-ticker.md`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 17
- Comment lines: 1
- Blank lines: 10

### Main Components

**Functions** (1):
- `test()`



## Usage Examples

### Main execution block:

```python
id = 'binance'
    symbol = 'ETH/BTC'
    pprint(asyncio.run(test(id, symbol)))
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

