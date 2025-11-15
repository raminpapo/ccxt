# Documentation: examples/py/coinone-markets.py

## File Metadata

- **Path**: `examples/py/coinone-markets.py`
- **Size**: 416 bytes
- **Lines**: 19
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

exchange = ccxt.coinone({
    # 'verbose': True,  # uncomment for verbose output
})

markets = exchange.load_markets()
pprint(markets)
print('\n', exchange.name, 'supports', len(markets), 'pairs')

```

## High-Level Overview

This is a Python file located at `examples/py/coinone-markets.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 11
- Comment lines: 2
- Blank lines: 6

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
python examples/py/coinone-markets.py
```

