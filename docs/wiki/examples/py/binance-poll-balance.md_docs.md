# Documentation: wiki/examples/py/binance-poll-balance.md

## File Metadata

- **Path**: `wiki/examples/py/binance-poll-balance.md`
- **Size**: 932 bytes
- **Lines**: 41
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Poll Balance](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-poll-balance.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 25
- Comment lines: 2
- Blank lines: 14

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

