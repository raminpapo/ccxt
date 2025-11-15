# Documentation: examples/ccxt.pro/py/bitmex_watch_ohlcv.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/bitmex_watch_ohlcv.py`
- **Size**: 1,654 bytes
- **Lines**: 42
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt.pro
from asyncio import run


def table(values):
    first = values[0]
    keys = list(first.keys()) if isinstance(first, dict) else range(0, len(first))
    widths = [max([len(str(v[k])) for v in values]) for k in keys]
    string = ' | '.join(['{:<' + str(w) + '}' for w in widths])
    return "\n".join([string.format(*[str(v[k]) for k in keys]) for v in values])


async def main():
    exchange = ccxt.pro.bitmex({
        # 'options': {
        #     'OHLCVLimit': 1000, # how many candles to store in memory by default
        # },
    })
    symbol = 'BTC/USD'
    timeframe = '1m'  # 5m, 1h, 1d
    limit = 10  # how many candles to return max
    method = 'watchOHLCV'
    if (method in exchange.has) and exchange.has[method]:
        max_iterations = 100  # how many times to repeat the loop before exiting
        for i in range(0, max_iterations):
            try:
                ohlcvs = await exchange.watch_ohlcv(symbol, timeframe, None, limit)
                now = exchange.milliseconds()
                print('\n===============================================================================')
                print('Loop iteration:', i, 'current time:', exchange.iso8601(now), symbol, timeframe)
                print('-------------------------------------------------------------------------------')
                print(table([[exchange.iso8601(o[0])] + o[1:] for o in ohlcvs]))
            except Exception as e:
                print(type(e).__name__, str(e))
                break
        await exchange.close()
    else:
        print(exchange.id, method, 'is not supported or not implemented yet')


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/bitmex_watch_ohlcv.py`.

**Functions defined**: main, table

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 32
- Comment lines: 3
- Blank lines: 7

### Main Components

**Functions** (2):
- `main()`
- `table()`



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
python examples/ccxt.pro/py/bitmex_watch_ohlcv.py
```

