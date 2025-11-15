# Documentation: wiki/examples/py/async-generator-multiple-tickers.md

## File Metadata

- **Path**: `wiki/examples/py/async-generator-multiple-tickers.md`
- **Size**: 542 bytes
- **Lines**: 28
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Generator Multiple Tickers](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import ccxt.async_support as ccxt


async def poll(tickers):
    i = 0
    kraken = ccxt.kraken()
    while True:
        symbol = tickers[i % len(tickers)]
        yield (symbol, await kraken.fetch_ticker(symbol))
        i += 1
        await asyncio.sleep(kraken.rateLimit / 1000)


async def main():
    async for (symbol, ticker) in poll(['BTC/USD', 'ETH/BTC', 'BTC/EUR']):
        print(symbol, ticker)


asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-generator-multiple-tickers.md`.

**Functions defined**: main, poll

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 17
- Comment lines: 1
- Blank lines: 10

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

