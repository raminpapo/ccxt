# Documentation: python/ccxt/static_dependencies/ethereum/account/encode_typed_data/helpers.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/ethereum/account/encode_typed_data/helpers.py`
- **Size**: 982 bytes
- **Lines**: 41
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from typing import (
    Any,
)

from ...utils import (
    is_hexstr,
)


def _get_eip712_solidity_types():
    types = ["bool", "address", "string", "bytes", "uint", "int"]
    ints = [f"int{(x + 1) * 8}" for x in range(32)]
    uints = [f"uint{(x + 1) * 8}" for x in range(32)]
    bytes_ = [f"bytes{x + 1}" for x in range(32)]
    return types + ints + uints + bytes_


EIP712_SOLIDITY_TYPES = _get_eip712_solidity_types()


def is_array_type(type_: str) -> bool:
    return type_.endswith("]")


def is_0x_prefixed_hexstr(value: Any) -> bool:
    return is_hexstr(value) and value.startswith("0x")


# strip all brackets: Person[][] -> Person
def parse_core_array_type(type_: str) -> str:
    if is_array_type(type_):
        type_ = type_[: type_.index("[")]
    return type_


# strip only last set of brackets: Person[3][1] -> Person[3]
def parse_parent_array_type(type_: str) -> str:
    if is_array_type(type_):
        type_ = type_[: type_.rindex("[")]
    return type_

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/ethereum/account/encode_typed_data/helpers.py`.

**Functions defined**: is_0x_prefixed_hexstr, is_array_type, parse_core_array_type, _get_eip712_solidity_types, parse_parent_array_type

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 25
- Comment lines: 2
- Blank lines: 14

### Main Components

**Functions** (5):
- `_get_eip712_solidity_types()`
- `is_0x_prefixed_hexstr()`
- `is_array_type()`
- `parse_core_array_type()`
- `parse_parent_array_type()`

**Constants** (1):
- `EIP712_SOLIDITY_TYPES`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/ethereum/account/encode_typed_data/helpers.py
```

