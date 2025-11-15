# Documentation: wiki/examples/py/async-bitfinex-public-get-symbols.md

## File Metadata

- **Path**: `wiki/examples/py/async-bitfinex-public-get-symbols.md`
- **Size**: 483 bytes
- **Lines**: 27
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Bitfinex Public Get Symbols](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402


async def test():
    bitfinex = ccxt.bitfinex({
        'apiKey': "YOUR_API_KEY",
        'secret': "YOUR_SECRET",
        'verbose': True,  # switch it to False if you don't want the HTTP log
    })
    print(await bitfinex.public_get_symbols())
    await bitfinex.close()


asyncio.run(test())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-bitfinex-public-get-symbols.md`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 16
- Comment lines: 1
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

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

