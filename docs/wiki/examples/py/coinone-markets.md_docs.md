# Documentation: wiki/examples/py/coinone-markets.md

## File Metadata

- **Path**: `wiki/examples/py/coinone-markets.md`
- **Size**: 353 bytes
- **Lines**: 22
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Coinone Markets](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402

exchange = ccxt.coinone({
    # 'verbose': True,  # uncomment for verbose output
})

markets = exchange.load_markets()
pprint(markets)
print('\n', exchange.name, 'supports', len(markets), 'pairs')
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/coinone-markets.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 12
- Comment lines: 2
- Blank lines: 8

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

