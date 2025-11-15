# Documentation: wiki/examples/py/binance-savings-endpoints.md

## File Metadata

- **Path**: `wiki/examples/py/binance-savings-endpoints.md`
- **Size**: 974 bytes
- **Lines**: 46
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Savings Endpoints](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

exchange = ccxt.binance({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

markets = exchange.load_markets()

exchange.verbose = True  # uncomment for debugging purposes

response = exchange.sapi_post_lending_customizedfixed_purchase({
    # YOUR PARAMS HERE
    # https://binance-docs.github.io/apidocs/spot/en/#purchase-fixed-activity-project-user_data
})

pprint(response)

response = exchange.sapi_post_lending_daily_purchase({
    # YOUR PARAMS HERE
    # https://binance-docs.github.io/apidocs/spot/en/#purchase-flexible-product-user_data
})

pprint(response)

response = exchange.sapi_post_lending_daily_redeem({
    # YOUR PARAMS HERE
    # https://binance-docs.github.io/apidocs/spot/en/#redeem-flexible-product-user_data
})

pprint(response) 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-savings-endpoints.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 23
- Comment lines: 7
- Blank lines: 16

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

