# Documentation: python/ccxt/static_dependencies/toolz/utils.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/toolz/utils.py`
- **Size**: 139 bytes
- **Lines**: 10
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
def raises(err, lamda):
    try:
        lamda()
        return False
    except err:
        return True


no_default = '__no__default__'

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/toolz/utils.py`.

**Functions defined**: raises



## Detailed Walkthrough

### Code Structure

- Total lines: 10
- Code lines: 7
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `raises()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/toolz/utils.py
```

