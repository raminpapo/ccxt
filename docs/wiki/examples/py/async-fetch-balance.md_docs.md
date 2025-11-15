# Documentation: wiki/examples/py/async-fetch-balance.md

## File Metadata

- **Path**: `wiki/examples/py/async-fetch-balance.md`
- **Size**: 871 bytes
- **Lines**: 34
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Fetch Balance](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402


async def test():
    exchange = ccxt.bitstamp({
        # "verbose": True,  # useful for debugging purposes, uncomment if needed
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        'uid': 'YOUR_UID',
        # i'm adding a CORS proxy here, because my country is blocked by bitstamp
        # you don't need this, so it's safe to comment it out
        # "proxy": "https://cors-anywhere.herokuapp.com/",
        # "origin": "bitstamp"
    })
    print(await exchange.fetch_balance())
    await exchange.close()  # don't forget to close it when you're done
    return True

if __name__ == '__main__':
    print('CCXT version:', ccxt.__version__)
    print(asyncio.run(test()))
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-fetch-balance.md`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 19
- Comment lines: 6
- Blank lines: 9

### Main Components

**Functions** (1):
- `test()`



## Usage Examples

### Main execution block:

```python
print('CCXT version:', ccxt.__version__)
    print(asyncio.run(test()))
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

