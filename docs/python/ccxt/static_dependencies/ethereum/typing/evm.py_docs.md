# Documentation: python/ccxt/static_dependencies/ethereum/typing/evm.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/ethereum/typing/evm.py`
- **Size**: 546 bytes
- **Lines**: 21
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from typing import (
    Literal,
    NewType,
    TypeVar,
    Union,
)

from .encoding import (
    HexStr,
)

Hash32 = NewType("Hash32", bytes)
BlockNumber = NewType("BlockNumber", int)
BlockParams = Literal["latest", "earliest", "pending", "safe", "finalized"]
BlockIdentifier = Union[BlockParams, BlockNumber, Hash32, HexStr, int]

Address = NewType("Address", bytes)
HexAddress = NewType("HexAddress", HexStr)
ChecksumAddress = NewType("ChecksumAddress", HexAddress)
AnyAddress = TypeVar("AnyAddress", Address, HexAddress, ChecksumAddress)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/ethereum/typing/evm.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 17
- Comment lines: 0
- Blank lines: 4

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
python python/ccxt/static_dependencies/ethereum/typing/evm.py
```

