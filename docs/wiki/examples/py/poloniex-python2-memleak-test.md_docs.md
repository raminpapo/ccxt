# Documentation: wiki/examples/py/poloniex-python2-memleak-test.md

## File Metadata

- **Path**: `wiki/examples/py/poloniex-python2-memleak-test.md`
- **Size**: 371 bytes
- **Lines**: 20
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Poloniex Python2 Memleak Test](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
import psutil


import ccxt  # noqa: E402
exchange = ccxt.poloniex()

while True:
    orderbook = exchange.fetch_order_book('ETH/BTC')
    process = psutil.Process(os.getpid())
    print(exchange.iso8601(exchange.milliseconds()), process.memory_info()[0])
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/poloniex-python2-memleak-test.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 12
- Comment lines: 1
- Blank lines: 7

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
