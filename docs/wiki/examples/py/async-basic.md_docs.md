# Documentation: wiki/examples/py/async-basic.md

## File Metadata

- **Path**: `wiki/examples/py/async-basic.md`
- **Size**: 378 bytes
- **Lines**: 25
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Basic](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402


async def test_binance():
    exchange = ccxt.binance()
    markets = await exchange.load_markets()
    await exchange.close()
    return markets


if __name__ == '__main__':
    print(asyncio.run(test_binance()))
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-basic.md`.

**Functions defined**: test_binance

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 14
- Comment lines: 1
- Blank lines: 10

### Main Components

**Functions** (1):
- `test_binance()`



## Usage Examples

### Main execution block:

```python
print(asyncio.run(test_binance()))
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

