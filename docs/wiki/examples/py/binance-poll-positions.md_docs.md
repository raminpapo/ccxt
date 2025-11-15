# Documentation: wiki/examples/py/binance-poll-positions.md

## File Metadata

- **Path**: `wiki/examples/py/binance-poll-positions.md`
- **Size**: 696 bytes
- **Lines**: 34
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Poll Positions](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-poll-positions.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 19
- Comment lines: 2
- Blank lines: 13

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

