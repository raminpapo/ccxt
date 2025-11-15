# Documentation: python/ccxt/static_dependencies/ethereum/utils/abi.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/ethereum/utils/abi.py`
- **Size**: 2,123 bytes
- **Lines**: 73
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from typing import (
    Any,
    Dict,
)

from .conversions import (
    to_bytes
)

from ...keccak import (
    SHA3 as keccak,
)


def collapse_if_tuple(abi: Dict[str, Any]) -> str:
    """
    Converts a tuple from a dict to a parenthesized list of its types.

    >>> from eth_utils.abi import collapse_if_tuple
    >>> collapse_if_tuple(
    ...     {
    ...         'components': [
    ...             {'name': 'anAddress', 'type': 'address'},
    ...             {'name': 'anInt', 'type': 'uint256'},
    ...             {'name': 'someBytes', 'type': 'bytes'},
    ...         ],
    ...         'type': 'tuple',
    ...     }
    ... )
    '(address,uint256,bytes)'
    """
    typ = abi["type"]
    if not isinstance(typ, str):
        raise TypeError(
            f"The 'type' must be a string, but got {repr(typ)} of type {type(typ)}"
        )
    elif not typ.startswith("tuple"):
        return typ

    delimited = ",".join(collapse_if_tuple(c) for c in abi["components"])
    # Whatever comes after "tuple" is the array dims. The ABI spec states that
    # this will have the form "", "[]", or "[k]".
    array_dim = typ[5:]
    collapsed = f"({delimited}){array_dim}"

    return collapsed


def _abi_to_signature(abi: Dict[str, Any]) -> str:
    fn_input_types = ",".join(
        [collapse_if_tuple(abi_input) for abi_input in abi.get("inputs", [])]
    )
    function_signature = f"{abi['name']}({fn_input_types})"
    return function_signature


def function_signature_to_4byte_selector(event_signature: str) -> bytes:
    return keccak(to_bytes(text=event_signature.replace(" ", "")))[:4]


def function_abi_to_4byte_selector(function_abi: Dict[str, Any]) -> bytes:
    function_signature = _abi_to_signature(function_abi)
    return function_signature_to_4byte_selector(function_signature)


def event_signature_to_log_topic(event_signature: str) -> bytes:
    return keccak(to_bytes(text=event_signature.replace(" ", "")))


def event_abi_to_log_topic(event_abi: Dict[str, Any]) -> bytes:
    event_signature = _abi_to_signature(event_abi)
    return event_signature_to_log_topic(event_signature)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/ethereum/utils/abi.py`.

**Functions defined**: function_abi_to_4byte_selector, function_signature_to_4byte_selector, event_abi_to_log_topic, _abi_to_signature, collapse_if_tuple, event_signature_to_log_topic

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 73
- Code lines: 53
- Comment lines: 4
- Blank lines: 16

### Main Components

**Functions** (6):
- `_abi_to_signature()`
- `collapse_if_tuple()`
- `event_abi_to_log_topic()`
- `event_signature_to_log_topic()`
- `function_abi_to_4byte_selector()`
- `function_signature_to_4byte_selector()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/ethereum/utils/abi.py
```

