# Documentation: examples/py/fetch-all-tickers.py

## File Metadata

- **Path**: `examples/py/fetch-all-tickers.py`
- **Size**: 2,250 bytes
- **Lines**: 73
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
import time
root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402


def print_exchanges():
    print('Supported exchanges:', ', '.join(ccxt.exchanges))


def print_usage():
    print("Usage: python", sys.argv[0], 'id')
    print("python", sys.argv[0], 'kraken')
    print("python", sys.argv[0], 'coinbasepro')
    print_exchanges()


try:

    id = sys.argv[1]  # get exchange id from command line arguments

    # check if the exchange is supported by ccxt
    exchange_found = id in ccxt.exchanges

    if exchange_found:

        print('Instantiating', id)

        # instantiate the exchange by id
        exchange = getattr(ccxt, id)()

        if exchange.has['fetchTickers'] != True:
            raise ccxt.NotSupported ('Exchange ' + exchange.id + ' does not have the endpoint to fetch all tickers from the API.')

        # load all markets from the exchange
        markets = exchange.load_markets()

        try:

            tickers = exchange.fetch_tickers()
            for symbol, ticker in tickers.items():
                print(
                    symbol,
                    ticker['datetime'],
                    'high: ' + str(ticker['high']),
                    'low: ' + str(ticker['low']),
                    'bid: ' + str(ticker['bid']),
                    'ask: ' + str(ticker['ask']),
                    'volume: ' + str(ticker['quoteVolume'] or ticker['baseVolume'])
                )

        except ccxt.DDoSProtection as e:
            print(type(e).__name__, e.args, 'DDoS Protection (ignoring)')
        except ccxt.RequestTimeout as e:
            print(type(e).__name__, e.args, 'Request Timeout (ignoring)')
        except ccxt.ExchangeNotAvailable as e:
            print(type(e).__name__, e.args, 'Exchange Not Available due to downtime or maintenance (ignoring)')
        except ccxt.AuthenticationError as e:
            print(type(e).__name__, e.args, 'Authentication Error (missing API keys, ignoring)')
    else:
        print('Exchange', id, 'not found')
        print_usage()

except Exception as e:

    print(type(e).__name__, e.args, str(e))
    print_usage()

```

## High-Level Overview

This is a Python file located at `examples/py/fetch-all-tickers.py`.

**Functions defined**: print_usage, print_exchanges

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 73
- Code lines: 48
- Comment lines: 4
- Blank lines: 21

### Main Components

**Functions** (2):
- `print_exchanges()`
- `print_usage()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/fetch-all-tickers.py
```

