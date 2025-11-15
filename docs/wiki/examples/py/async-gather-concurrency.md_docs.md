# Documentation: wiki/examples/py/async-gather-concurrency.md

## File Metadata

- **Path**: `wiki/examples/py/async-gather-concurrency.md`
- **Size**: 2,146 bytes
- **Lines**: 78
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Gather Concurrency](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402


async def work(exchange_id):

    # create it once per program lifetime
    exchange = getattr(ccxt, exchange_id)()

    print(exchange_id, 'loaded')

    try:

        # load markets once, first and foremost
        # https://github.com/ccxt/ccxt/wiki/Manual#loading-markets
        await exchange.load_markets()

        # use the same exchange instance to iterate over loaded symbols
        # https://github.com/ccxt/ccxt/wiki/Manual#symbols-and-market-ids

        for symbol in exchange.symbols:

            try:

                # fetch the orderbook for each next symbol
                orderbook = await exchange.fetch_order_book(symbol)

                # ADD YOUR SUCCESS HANDLING HERE
                print(exchange_id, 'fetched', symbol, 'orderbook')

            except Exception as e:

                # ADD YOUR ERROR HANDLING HERE
                # https://github.com/ccxt/ccxt/wiki/Manual#error-handling
                print(exchange_id, 'could not fetch', symbol, 'orderbook:', type(e).__name__)

    except Exception as e:

        # ADD YOUR ERROR HANDLING HERE
        print(exchange_id, 'could not load markets:', type(e).__name__)

    # when you're done, don't forget to close the exchange instance properly
    # otherwise you will get "Unclosed client session" exception
    await exchange.close()


async def main():

    # https://stackoverflow.com/questions/48483348/limited-concurrency-with-asyncio
    max_concurrency = 5  # how many exchanges at once

    tasks = set()
    loop = asyncio.get_running_loop()
    # loop over all exchanges
    for exchange_id in ccxt.exchanges:

        # wait for some exchange to finish before adding a new one
        if len(tasks) >= max_concurrency:
            _done, tasks = await asyncio.wait(tasks, return_when=asyncio.FIRST_COMPLETED)
        tasks.add(loop.create_task(work(exchange_id)))

    # wait for the remaining exchanges to finish
    await asyncio.wait(tasks)


asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-gather-concurrency.md`.

**Functions defined**: work, main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 78
- Code lines: 31
- Comment lines: 17
- Blank lines: 30

### Main Components

**Functions** (2):
- `main()`
- `work()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

