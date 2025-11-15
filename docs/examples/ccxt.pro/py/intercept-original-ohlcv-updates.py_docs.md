# Documentation: examples/ccxt.pro/py/intercept-original-ohlcv-updates.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/intercept-original-ohlcv-updates.py`
- **Size**: 880 bytes
- **Lines**: 32
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from asyncio import run
import ccxt.pro
from pprint import pprint


class MyBinance(ccxt.pro.binance):
    def handle_ohlcv(self, client, message):
        # add your handling of the original message here
        print('intercepted', message)
        return super(MyBinance, self).handle_ohlcv(client, message)


async def main():
    exchange = MyBinance()
    symbol = 'BTC/USDT'
    print('Watching', exchange.id, symbol)
    while True:
        try:
            ohlcv = await exchange.watch_ohlcv(symbol, '1m')
        except Exception as e:
            print(str(e))
            # raise e  # uncomment to break all loops in case of an error in any one of them
            # break  # you can also break just this one loop if it fails
    await exchange.close()


if __name__ == "__main__":
    print('CCXT Version:', ccxt.__version__)
    run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/intercept-original-ohlcv-updates.py`.

**Classes defined**: MyBinance

**Functions defined**: handle_ohlcv, main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 20
- Comment lines: 4
- Blank lines: 8

### Main Components

**Classes** (1):
- `MyBinance`

**Functions** (2):
- `handle_ohlcv()`
- `main()`



## Usage Examples

### Main execution block:

```python
print('CCXT Version:', ccxt.__version__)
    run(main())
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/ccxt.pro/py/intercept-original-ohlcv-updates.py
```

