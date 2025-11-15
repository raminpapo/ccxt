# Documentation: examples/py/fetch-order-book-rtt.py

## File Metadata

- **Path**: `examples/py/fetch-order-book-rtt.py`
- **Size**: 1,656 bytes
- **Lines**: 57
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402


# WARNING!
# This example measures the round-trip time by fetching the orderbook from an exchange
# In order to measure the speed of requests it disables the rate-limiting
# Disabling the rate-limiter is required to do an accurate measurement
# If you keep running without a rate limiter for a long time the exchange will ban you
# In a live production system always use either the built-in rate limiter or make your own


def main():

    # the exchange instance has to be reused
    # do not recreate the exchange before each call!

    exchange = ccxt.binance({

        # if you do not rate-limit your requests the exchange can ban you!
        'enableRateLimit': False,  # https://github.com/ccxt/ccxt/wiki/Manual#rate-limit

    })

    exchange.load_markets()  # https://github.com/ccxt/ccxt/wiki/Manual#loading-markets

    # exchange.verbose = True  # uncomment for debugging purposes if needed

    symbol = 'BTC/USDT'

    results = []
    num_iterations = 50

    for i in range(0, num_iterations):
        started = exchange.milliseconds()
        orderbook = exchange.fetch_order_book(symbol)
        ended = exchange.milliseconds()
        elapsed = ended - started
        print(elapsed, 'ms')
        results.append(elapsed)

    pprint(results)

    rtt = int(sum(results) / len(results))
    print('Successfully tested', num_iterations, 'calls, the average round-trip time per call is', rtt, 'milliseconds')


main()

```

## High-Level Overview

This is a Python file located at `examples/py/fetch-order-book-rtt.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 57
- Code lines: 25
- Comment lines: 11
- Blank lines: 21

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/fetch-order-book-rtt.py
```

