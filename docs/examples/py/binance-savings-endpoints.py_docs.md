# Documentation: examples/py/binance-savings-endpoints.py

## File Metadata

- **Path**: `examples/py/binance-savings-endpoints.py`
- **Size**: 1,027 bytes
- **Lines**: 43
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

## High-Level Overview

This is a Python file located at `examples/py/binance-savings-endpoints.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 22
- Comment lines: 7
- Blank lines: 14

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
python examples/py/binance-savings-endpoints.py
```

