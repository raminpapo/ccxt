# Documentation: examples/ccxt.pro/py/build-ohlcv-many-symbols.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/build-ohlcv-many-symbols.py`
- **Size**: 2,025 bytes
- **Lines**: 54
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-
import asyncio
import ccxt.pro


print('CCXT Version:', ccxt.__version__)


async def loop(exchange, symbol, timeframe, complete_candles_only=False):
    duration_in_seconds = exchange.parse_timeframe(timeframe)
    duration_in_ms = duration_in_seconds * 1000
    while True:
        try:
            trades = await exchange.watch_trades(symbol)
            if len(trades) > 0:
                current_minute = int(exchange.milliseconds() / duration_in_ms)
                ohlcvc = exchange.build_ohlcvc(trades, timeframe)
                if complete_candles_only:
                    ohlcvc = [candle for candle in ohlcvc if int(candle[0] / duration_in_ms) < current_minute]
                if len(ohlcvc) > 0:
                    print('-----------------------------------------------------------')
                    print("Symbol:", symbol, "timeframe:", timeframe)
                    print(ohlcvc)

        except Exception as e:
            print(f"{type(e).__name__}: {(str(e))}")
            # raise type(e)(str(e))  # uncomment to break all loops in case of an error in any one of them
            # break  # you can also break just this one loop if it fails


async def main():
    # select the exchange
    exchange = ccxt.pro.binance()
    if exchange.has['watchTrades']:
        markets = await exchange.load_markets()
        # Change this value accordingly
        timeframe = '1m'
        limit = 5
        selected_symbols = list(markets.values())[:limit]
        # you can also specify the symbols manually
        # selected_symbols = ['BTC/USDT', 'ETH/USDT']

        # Use this variable to choose if only complete candles
        # should be considered
        complete_candles_only = True
        await asyncio.gather(*[loop(exchange, symbol['symbol'], timeframe, complete_candles_only)
                               for symbol in selected_symbols])
        await exchange.close()
    else:
        print(exchange.id, 'does not support watchTrades yet')


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/build-ohlcv-many-symbols.py`.

**Functions defined**: loop, main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 34
- Comment lines: 9
- Blank lines: 11

### Main Components

**Functions** (2):
- `loop()`
- `main()`



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
python examples/ccxt.pro/py/build-ohlcv-many-symbols.py
```

