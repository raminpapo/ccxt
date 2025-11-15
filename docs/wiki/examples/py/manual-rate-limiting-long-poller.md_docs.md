# Documentation: wiki/examples/py/manual-rate-limiting-long-poller.md

## File Metadata

- **Path**: `wiki/examples/py/manual-rate-limiting-long-poller.md`
- **Size**: 727 bytes
- **Lines**: 28
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Manual Rate Limiting Long Poller](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
import time


import ccxt  # noqa: E402

# if you imported the ccxt library with `import ccxt` you can
# throttle your requests manually, by using the rateLimit property of an exchange
# to delay each request by waiting for some time to stay below request rate limits

exchange = ccxt.bitfinex()

# the rateLimit is in milliseconds → divide it by a thousand to get seconds
delay = exchange.rateLimit / 1000

for i in range(0, 10):
    # this can be any call instead of fetch_ticker, really
    print(exchange.fetch_ticker('BTC/USD'))
    time.sleep(delay)  # sleep a little before sending each next request
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/manual-rate-limiting-long-poller.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 12
- Comment lines: 6
- Blank lines: 10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

