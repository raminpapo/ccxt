# Documentation: wiki/examples/py/binance-universal-transfer.md

## File Metadata

- **Path**: `wiki/examples/py/binance-universal-transfer.md`
- **Size**: 743 bytes
- **Lines**: 33
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Universal Transfer](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-universal-transfer.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 19
- Comment lines: 2
- Blank lines: 12

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

**To execute this Markdown file:**

