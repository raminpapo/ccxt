# Documentation: python/ccxt/static_dependencies/starknet/hash/storage.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/hash/storage.py`
- **Size**: 402 bytes
- **Lines**: 13
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from functools import reduce

from constants import ADDR_BOUND
from hash.utils import _starknet_keccak, pedersen_hash


def get_storage_var_address(var_name: str, *args: int) -> int:
    """
    Returns the storage address of a Starknet storage variable given its name and arguments.
    """
    res = _starknet_keccak(var_name.encode("ascii"))
    return reduce(pedersen_hash, args, res) % ADDR_BOUND

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/hash/storage.py`.

**Functions defined**: get_storage_var_address

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 13
- Code lines: 9
- Comment lines: 2
- Blank lines: 2

### Main Components

**Functions** (1):
- `get_storage_var_address()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/hash/storage.py
```

