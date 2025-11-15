# Documentation: wiki/examples/py/instantiate-all-at-once.md

## File Metadata

- **Path**: `wiki/examples/py/instantiate-all-at-once.md`
- **Size**: 392 bytes
- **Lines**: 22
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Instantiate All At Once](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402

exchanges = {}  # a placeholder for your instances

for id in ccxt.exchanges:
    exchange = getattr(ccxt, id)
    exchanges[id] = exchange()

# now exchanges dictionary contains all exchange instances...
exchanges['bittrex'].fetch_order_book('ETH/BTC')
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/instantiate-all-at-once.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 11
- Comment lines: 2
- Blank lines: 9

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

