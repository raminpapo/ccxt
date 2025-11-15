# Documentation: examples/ccxt.pro/py/gateio-watch-trades.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/gateio-watch-trades.py`
- **Size**: 656 bytes
- **Lines**: 26
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import ccxt.pro

from datetime import datetime

async def loop(exchange, symbol):
    since = datetime.utcnow()
    timestamp = int(since.timestamp() * 1000)
    while True:
        trades = await exchange.watch_trades(symbol, since=timestamp)
        print('--------------------------------------------------------------')
        print('Received', len(trades), 'after', exchange.iso8601 (timestamp))
        print('waiting for next update...')


async def main():
    exchange = ccxt.pro.gateio()
    await loop(exchange, 'BTC/USDT')
    await exchange.close()


if __name__ == '__main__':
    asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/gateio-watch-trades.py`.

**Functions defined**: loop, main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 17
- Comment lines: 1
- Blank lines: 8

### Main Components

**Functions** (2):
- `loop()`
- `main()`



## Usage Examples

### Main execution block:

```python
asyncio.run(main())
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/ccxt.pro/py/gateio-watch-trades.py
```

