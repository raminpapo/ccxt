# Documentation: examples/py/binance-universal-transfer.py

## File Metadata

- **Path**: `examples/py/binance-universal-transfer.py`
- **Size**: 795 bytes
- **Lines**: 30
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


def main():

    # apiKey must have universal transfer permissions
    binance = ccxt.binance({
        "apiKey": "YOUR_API_KEY",
        "secret": "YOUR_SECRET",
    })
    binance.load_markets()

    pprint(binance.transfer('USDT', 0.1, 'spot', 'future'))
    transfers = binance.fetch_transfers()
    pprint('there is ' + str(len(transfers)) + ' transfers')
    pprint(binance.transfer('USDT', 0.1, 'spot', 'cross'))  # For transfer to cross margin wallet
    pprint(binance.transfer('USDT', 0.1, 'spot', 'ADA/USDT'))  # For transfer to an isolated margin wallet


main()

```

## High-Level Overview

This is a Python file located at `examples/py/binance-universal-transfer.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 18
- Comment lines: 2
- Blank lines: 10

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
python examples/py/binance-universal-transfer.py
```

