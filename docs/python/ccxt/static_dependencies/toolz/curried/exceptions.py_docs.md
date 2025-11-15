# Documentation: python/ccxt/static_dependencies/toolz/curried/exceptions.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/toolz/curried/exceptions.py`
- **Size**: 344 bytes
- **Lines**: 23
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from .. import (
    curry,
    merge_with,
    merge
)


__all__ = ['merge_with', 'merge']


@curry
def merge_with(func, d, *dicts, **kwargs):
    return merge_with(func, d, *dicts, **kwargs)


@curry
def merge(d, *dicts, **kwargs):
    return merge(d, *dicts, **kwargs)


merge_with.__doc__ = merge_with.__doc__
merge.__doc__ = merge.__doc__

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/toolz/curried/exceptions.py`.

**Functions defined**: merge, merge_with

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 14
- Comment lines: 0
- Blank lines: 9

### Main Components

**Functions** (2):
- `merge()`
- `merge_with()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/toolz/curried/exceptions.py
```

