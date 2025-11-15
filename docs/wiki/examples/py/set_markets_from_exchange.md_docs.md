# Documentation: wiki/examples/py/set_markets_from_exchange.md

## File Metadata

- **Path**: `wiki/examples/py/set_markets_from_exchange.md`
- **Size**: 1,198 bytes
- **Lines**: 47
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Set_markets_from_exchange](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402
import psutil  # noqa: E402


def get_memory_usage():
    """Get current memory usage in MB"""
    process = psutil.Process()
    memory_info = process.memory_info()
    return memory_info.rss / 1024 / 1024  # Convert to MB


async def test():
    print(f"Initial memory usage: {get_memory_usage():.2f} MB")
    
    binance = ccxt.binance({})
    print(f"Memory usage after creating binance: {get_memory_usage():.2f} MB")
    
    await binance.load_markets()
    print(f"Memory usage after loading markets: {get_memory_usage():.2f} MB")
    
    binance2 = ccxt.binance({})
    print(f"Memory usage after creating binance2: {get_memory_usage():.2f} MB")
    
    binance2.set_markets_from_exchange(binance)
    print(f"Memory usage after setting markets from exchange: {get_memory_usage():.2f} MB")
    print (f"binance2.symbols loaded: {len(binance2.symbols)}")
    
    await binance.close()
    await binance2.close()
    print(f"Final memory usage after closing: {get_memory_usage():.2f} MB")


asyncio.run(test())

 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/set_markets_from_exchange.md`.

**Functions defined**: test, get_memory_usage

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 28
- Comment lines: 2
- Blank lines: 17

### Main Components

**Functions** (2):
- `get_memory_usage()`
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

