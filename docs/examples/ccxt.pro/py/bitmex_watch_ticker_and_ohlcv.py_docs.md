# Documentation: examples/ccxt.pro/py/bitmex_watch_ticker_and_ohlcv.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/bitmex_watch_ticker_and_ohlcv.py`
- **Size**: 2,959 bytes
- **Lines**: 74
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt.pro
from asyncio import run, gather


def table(values):
    first = values[0]
    keys = list(first.keys()) if isinstance(first, dict) else range(0, len(first))
    widths = [max([len(str(v[k])) for v in values]) for k in keys]
    string = ' | '.join(['{:<' + str(w) + '}' for w in widths])
    return "\n".join([string.format(*[str(v[k]) for k in keys]) for v in values])


async def watch_ticker(color, duration, exchange, symbol):
    method = 'watchTicker'
    if (method in exchange.has) and exchange.has[method]:
        start = exchange.milliseconds()
        i = 1
        while True:
            ticker = await exchange.watch_ticker(symbol)
            now = exchange.milliseconds()
            # start color code
            print(color, 'Ticker ========================================================================')
            print(exchange.iso8601(now), symbol, 'iteration:', i, 'last price:', ticker['last'])
            print('-------------------------------------------------------------------------------')
            # pprint.pprint(ticker)  # uncomment for a lengthy complete printout
            print('\x1b[0m')  # stop color code
            i += 1
            if (start + duration) < now:
                break
    else:
        raise Exception(exchange.id + ' ' + method + ' is not supported or not implemented yet')


async def watch_ohlcv(color, duration, exchange, symbol, timeframe, limit):
    method = 'watchOHLCV'
    if (method in exchange.has) and exchange.has[method]:
        start = exchange.milliseconds()
        i = 1
        while True:
            ohlcvs = await exchange.watch_ohlcv(symbol, timeframe, None, limit)
            now = exchange.milliseconds()
            # start color code
            print(color, 'OHLCV =========================================================================')
            print(exchange.iso8601(now), symbol, timeframe, 'iteration:', i)
            print('-------------------------------------------------------------------------------')
            print(table([[exchange.iso8601(o[0])] + o[1:] for o in ohlcvs]))
            print('\x1b[0m')  # stop color code
            i += 1
            if (start + duration) < now:
                break
    else:
        raise Exception(exchange.id + ' ' + method + ' is not supported or not implemented yet')


# =============================================================================


async def main():
    exchange = ccxt.pro.bitmex()
    await exchange.load_markets()
    duration = 1200000  # run 20 minutes = 1200000 milliseconds
    symbol = 'BTC/USD'
    limit = 10
    loops = [
        watch_ticker('\033[35m', duration, exchange, symbol),              # magenta
        watch_ohlcv('\x1b[33m', duration, exchange, symbol, '1m', limit),  # yellow
        watch_ohlcv('\x1b[32m', duration, exchange, symbol, '5m', limit),  # green
    ]
    await gather(*loops)
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/bitmex_watch_ticker_and_ohlcv.py`.

**Functions defined**: main, watch_ticker, watch_ohlcv, table

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 74
- Code lines: 57
- Comment lines: 4
- Blank lines: 13

### Main Components

**Functions** (4):
- `main()`
- `table()`
- `watch_ohlcv()`
- `watch_ticker()`

**Constants** (1):
- `OHLCV`



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
python examples/ccxt.pro/py/bitmex_watch_ticker_and_ohlcv.py
```

