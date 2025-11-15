# Documentation: examples/py/binance-poll-positions.py

## File Metadata

- **Path**: `examples/py/binance-poll-positions.py`
- **Size**: 752 bytes
- **Lines**: 31
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)


exchange = ccxt.binanceusdm({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})
markets = exchange.load_markets()

# exchange.verbose = True  # uncomment for debugging purposes if necessary

while True:
    try:
        positions = exchange.fetch_positions ()
        print(exchange.iso8601(exchange.milliseconds()), len(positions), 'positions')
        print([ [position['symbol'], position['contracts']] for position in positions ])
    except Exception as e:
        print(type(e).__name__, str(e))


```

## High-Level Overview

This is a Python file located at `examples/py/binance-poll-positions.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 18
- Comment lines: 2
- Blank lines: 11

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
python examples/py/binance-poll-positions.py
```

