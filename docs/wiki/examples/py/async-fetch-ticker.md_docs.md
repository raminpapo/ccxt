# Documentation: wiki/examples/py/async-fetch-ticker.md

## File Metadata

- **Path**: `wiki/examples/py/async-fetch-ticker.md`
- **Size**: 256 bytes
- **Lines**: 17
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Fetch Ticker](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys
from pprint import pprint


import ccxt.async_support as ccxt  # noqa: E402

pprint(asyncio.run(ccxt.binance().fetch_ticker('ETH/BTC')))
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-fetch-ticker.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 9
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

**To execute this Markdown file:**

