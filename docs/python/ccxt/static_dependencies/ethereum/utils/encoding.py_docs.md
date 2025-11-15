# Documentation: python/ccxt/static_dependencies/ethereum/utils/encoding.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/ethereum/utils/encoding.py`
- **Size**: 199 bytes
- **Lines**: 7
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
def int_to_big_endian(value: int) -> bytes:
    return value.to_bytes((value.bit_length() + 7) // 8 or 1, "big")


def big_endian_to_int(value: bytes) -> int:
    return int.from_bytes(value, "big")

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/ethereum/utils/encoding.py`.

**Functions defined**: big_endian_to_int, int_to_big_endian



## Detailed Walkthrough

### Code Structure

- Total lines: 7
- Code lines: 4
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (2):
- `big_endian_to_int()`
- `int_to_big_endian()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/ethereum/utils/encoding.py
```

