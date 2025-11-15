# Documentation: wiki/examples/py/exchange-save-load-markets-cache.md

## File Metadata

- **Path**: `wiki/examples/py/exchange-save-load-markets-cache.md`
- **Size**: 1,761 bytes
- **Lines**: 81
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Exchange Save Load Markets Cache](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
from random import randint
import sys
from pprint import pprint


import ccxt.pro as ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

exchange = ccxt.bybit({
    # 'apiKey': 'YOUR_API_KEY',
    # 'secret': 'YOUR_SECRET_KEY',
})

cache = {} # in this example we will save markets cache in this variable, but it can be saved in a file or database

# We should use this strategy, when we need to recreate the exchange instance
# multiple times, but we don't want to reload the cache every time
# to avoid the extra time and resources needed to load the markets cache


async def save_markets_cache():
    global cache
    before = exchange.milliseconds()

    markets = await exchange.load_markets()

    after = exchange.milliseconds()

    print("Time to load markets:", after - before, "ms")

    currencies = exchange.currencies

    cache['markets'] = markets
    cache['currencies'] = currencies


async def instantiate_with_cache():
    global cache

    new_instance = ccxt.bybit({
        'markets': cache['markets'],
        'currencies': cache['currencies']
    })

    before = exchange.milliseconds()

    await new_instance.load_markets()

    after = exchange.milliseconds()

    print ("Time to load markets with cache:", after - before, "ms") # as you can see, it is instanteous

async def main():
    try:
        await save_markets_cache()

        await instantiate_with_cache()

    except Exception as e:
        print(e)
    await exchange.close()


asyncio.run(main())


# it should output something like this
# CCXT Version: 4.4.38
# Time to load markets: 1582 ms
# Time to load markets with cache: 0 ms 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/exchange-save-load-markets-cache.md`.

**Functions defined**: instantiate_with_cache, save_markets_cache, main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 81
- Code lines: 40
- Comment lines: 10
- Blank lines: 31

### Main Components

**Functions** (3):
- `instantiate_with_cache()`
- `main()`
- `save_markets_cache()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations
- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

