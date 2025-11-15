# Documentation: examples/ccxt.pro/py/multiple-exchanges-watch-orderbook-continuously.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/multiple-exchanges-watch-orderbook-continuously.py`
- **Size**: 1,178 bytes
- **Lines**: 35
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt.pro
import asyncio
import time


async def watch_book(exchange, ticker):
    last = None
    while True:
        try:
            orderbook = await exchange.watch_order_book(ticker)
            # TODO add timeout within a minute
            # TODO add last
            top_bid = orderbook['bids'][0][0]
            if last != top_bid:
                print(f'{int(time.time() * 1000)} top bid for celo on {exchange.name} is {top_bid}')
            last = top_bid
        except Exception as e:
            print(f'{exchange.name} failed {type(e)} {e}')


async def main():
    exchange_ids = ['coinbasepro', 'okcoin', 'bittrex']
    exchanges = [getattr(ccxt.pro, exchange_id)() for exchange_id in exchange_ids]
    try:
        done, pending = await asyncio.wait({watch_book(exchange, 'CELO/USD') for exchange in exchanges}, return_when=asyncio.FIRST_EXCEPTION)
        for completed in done:
            # trigger the exception here
            completed.result()
    except Exception as e:
        print(f'closing all exchanges because of exception {type(e)} {e}')
        await asyncio.gather(*[exchange.close() for exchange in exchanges])


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/multiple-exchanges-watch-orderbook-continuously.py`.

**Functions defined**: main, watch_book

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 25
- Comment lines: 3
- Blank lines: 7

### Main Components

**Functions** (2):
- `main()`
- `watch_book()`



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
python examples/ccxt.pro/py/multiple-exchanges-watch-orderbook-continuously.py
```

