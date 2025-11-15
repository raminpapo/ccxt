# Documentation: python/ccxt/static_dependencies/ethereum/abi/abi.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/ethereum/abi/abi.py`
- **Size**: 490 bytes
- **Lines**: 20
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from .codec import (
    ABICodec,
)
from .registry import (
    registry,
)

default_codec = ABICodec(registry)

encode = default_codec.encode
encode_abi = default_codec.encode_abi  # deprecated
encode_single = default_codec.encode_single  # deprecated

decode = default_codec.decode
decode_abi = default_codec.decode_abi  # deprecated
decode_single = default_codec.decode_single  # deprecated

is_encodable = default_codec.is_encodable
is_encodable_type = default_codec.is_encodable_type

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/ethereum/abi/abi.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 15
- Comment lines: 0
- Blank lines: 5

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
python python/ccxt/static_dependencies/ethereum/abi/abi.py
```

