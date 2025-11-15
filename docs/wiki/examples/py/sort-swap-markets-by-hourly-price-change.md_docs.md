# Documentation: wiki/examples/py/sort-swap-markets-by-hourly-price-change.md

## File Metadata

- **Path**: `wiki/examples/py/sort-swap-markets-by-hourly-price-change.md`
- **Size**: 2,139 bytes
- **Lines**: 75
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Sort Swap Markets By Hourly Price Change](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
import asyncio
import time
from pprint import pprint
from datetime import datetime

import ccxt.async_support as ccxt  # noqa: E402
exchange = ccxt.binanceusdm()
timeframe = '1h'
ohlcvs = []


async def fetchOHLCV(symbol):
    '''
    Wrapper around exchange.fetchOHLCV method
    :param str symbol: CCXT unified symbol
    :returns [float|str]: 1d array with a single ohlcv record with the market symbol appended
    '''
    try:
        ohlcv = await exchange.fetchOHLCV(symbol, timeframe, None, 2)
        ohlcv[0].append(symbol)
        ohlcvs.append(ohlcv[0])
    except Exception as e:
        print(f'{symbol} failed fetchOHLCV with exception {e}')


def getPriceChangePercent(ohlcv):
    '''
    Gets the price change of a market as a percentage
    :param [float] ohlcv: A single ohlcv record with the market symbol appended
    :returns [float, str]: The price change as a percent with the symbol for the market
    '''
    open = ohlcv[1]
    close = ohlcv[4]
    symbol = ohlcv[6]
    priceIncrease = close - open
    increaseAsRatio = priceIncrease / open
    return [increaseAsRatio, symbol]


async def main():
    '''
    Gets the price change as a percent of every market matching type over the last timeframe matching timeframe and prints a sorted list.
    The most immediate candle is ignored because it is incomplete
    '''
    start = time.time()

    await exchange.load_markets()
    allSwapSymbols = [symbol for symbol in exchange.symbols if exchange.market(symbol)['swap']]
    await asyncio.gather(*[fetchOHLCV(symbol) for symbol in allSwapSymbols])
    await exchange.close()
    priceChanges = [getPriceChangePercent(ohlcv) for ohlcv in ohlcvs]
    priceChanges.sort()

    end = time.time()
    duration = str(int((end - start) * 1000))
    now = str(datetime.utcnow().isoformat())

    print('python', sys.version)
    print('CCXT Version:', ccxt.__version__)
    print(now + ' iteration 0 passed in ' + duration + ' ms')
    print()
    pprint(priceChanges)


asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/sort-swap-markets-by-hourly-price-change.md`.

**Functions defined**: getPriceChangePercent, main, fetchOHLCV

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 75
- Code lines: 58
- Comment lines: 7
- Blank lines: 10

### Main Components

**Functions** (3):
- `fetchOHLCV()`
- `getPriceChangePercent()`
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

