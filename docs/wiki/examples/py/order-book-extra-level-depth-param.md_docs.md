# Documentation: wiki/examples/py/order-book-extra-level-depth-param.md

## File Metadata

- **Path**: `wiki/examples/py/order-book-extra-level-depth-param.md`
- **Size**: 277 bytes
- **Lines**: 17
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Order Book Extra Level Depth Param](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402

# return up to ten bidasks on each side of the order book stack
limit = 10
print(ccxt.cex().fetch_order_book('BTC/USD', limit))
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/order-book-extra-level-depth-param.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 8
- Comment lines: 2
- Blank lines: 7

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

