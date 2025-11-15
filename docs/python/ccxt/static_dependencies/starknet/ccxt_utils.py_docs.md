# Documentation: python/ccxt/static_dependencies/starknet/ccxt_utils.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/ccxt_utils.py`
- **Size**: 340 bytes
- **Lines**: 7
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# utils to use starknet library in ccxt
from .constants import EC_ORDER
from ..starkware.crypto.signature import grind_key

def get_private_key_from_eth_signature(eth_signature_hex: str) -> int:
    r = eth_signature_hex[2 : 64 + 2] if eth_signature_hex[0:2] == '0x' else eth_signature_hex[0 : 64]
    return grind_key(int(r, 16), EC_ORDER)
```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/ccxt_utils.py`.

**Functions defined**: get_private_key_from_eth_signature

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 7
- Code lines: 5
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (1):
- `get_private_key_from_eth_signature()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/ccxt_utils.py
```

