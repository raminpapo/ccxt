# Documentation: python/ccxt/abstract/hyperliquid.py

## File Metadata

- **Path**: `python/ccxt/abstract/hyperliquid.py`
- **Size**: 394 bytes
- **Lines**: 7
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_post_info = publicPostInfo = Entry('info', 'public', 'POST', {'cost': 20, 'byType': {'l2Book': 2, 'allMids': 2, 'clearinghouseState': 2, 'orderStatus': 2, 'spotClearinghouseState': 2, 'exchangeStatus': 2, 'candleSnapshot': 4}})
    private_post_exchange = privatePostExchange = Entry('exchange', 'private', 'POST', {'cost': 1})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/hyperliquid.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 7
- Code lines: 4
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `ImplicitAPI`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/abstract/hyperliquid.py
```

