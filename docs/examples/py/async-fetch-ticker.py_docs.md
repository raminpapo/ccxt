# Documentation: examples/py/async-fetch-ticker.py

## File Metadata

- **Path**: `examples/py/async-fetch-ticker.py`
- **Size**: 316 bytes
- **Lines**: 14
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import os
import sys
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402

pprint(asyncio.run(ccxt.binance().fetch_ticker('ETH/BTC')))

```

## High-Level Overview

This is a Python file located at `examples/py/async-fetch-ticker.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 8
- Comment lines: 1
- Blank lines: 5

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
python examples/py/async-fetch-ticker.py
```

