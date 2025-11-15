# Documentation: python/ccxt/static_dependencies/ethereum/typing/bls.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/ethereum/typing/bls.py`
- **Size**: 191 bytes
- **Lines**: 8
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from typing import (
    NewType,
)

BLSPubkey = NewType("BLSPubkey", bytes)  # bytes48
BLSPrivateKey = NewType("BLSPrivateKey", int)
BLSSignature = NewType("BLSSignature", bytes)  # bytes96

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/ethereum/typing/bls.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 8
- Code lines: 6
- Comment lines: 0
- Blank lines: 2

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
python python/ccxt/static_dependencies/ethereum/typing/bls.py
```

