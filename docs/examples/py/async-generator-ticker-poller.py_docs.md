# Documentation: examples/py/async-generator-ticker-poller.py

## File Metadata

- **Path**: `examples/py/async-generator-ticker-poller.py`
- **Size**: 766 bytes
- **Lines**: 30
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402


async def poll():
    kraken = ccxt.kraken({
        'apiKey': "hEvQNMDIeoCJbr7W/ZBb5CGOrx3G0lWF5B3zqa1JBxdZlEaL8EK+D0Mw",
        'secret': "JaE9wI6Nwgh5oRxiHcVxurwzwBxwc05W/qv/k1srGg4s3EYuXPpNkLLM5NYbbWpM8rCyijIeDavRuqWbU0ZV9A==",
        # 'verbose': True, # switch it to False if you don't want the HTTP log
    })
    while True:
        yield await kraken.fetch_ticker('BTC/USD')
        await asyncio.sleep(kraken.rateLimit / 1000)


async def main():
    async for ticker in poll():
        print(ticker)


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/async-generator-ticker-poller.py`.

**Functions defined**: main, poll

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 18
- Comment lines: 2
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

**To execute this Python file:**

```bash
python examples/py/async-generator-ticker-poller.py
```

