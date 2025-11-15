# Documentation: examples/py/binance-poll-balance.py

## File Metadata

- **Path**: `examples/py/binance-poll-balance.py`
- **Size**: 990 bytes
- **Lines**: 38
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


print('CCXT Version:', ccxt.__version__)


exchange = ccxt.binance({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

markets = exchange.load_markets()

# exchange.verbose = True  # uncomment for debugging purposes if necessary

previous_timestamp = exchange.milliseconds()
while True:
    try:
        balance = exchange.fetch_balance()
        print('--------------------------------------------------------------')
        current_timestamp = exchange.milliseconds()
        print(exchange.iso8601(current_timestamp), 'balance:')
        pprint(balance)
        print('Fetched in', current_timestamp - previous_timestamp, 'milliseconds')
        previous_timestamp = current_timestamp
    except Exception as e:
        print(type(e).__name__, str(e))


```

## High-Level Overview

This is a Python file located at `examples/py/binance-poll-balance.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 24
- Comment lines: 2
- Blank lines: 12

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/binance-poll-balance.py
```

