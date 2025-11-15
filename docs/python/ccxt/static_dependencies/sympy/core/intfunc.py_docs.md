# Documentation: python/ccxt/static_dependencies/sympy/core/intfunc.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/sympy/core/intfunc.py`
- **Size**: 844 bytes
- **Lines**: 36
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
"""
The routines here were removed from numbers.py, power.py,
digits.py and factor_.py so they could be imported into core
without raising circular import errors.

Although the name 'intfunc' was chosen to represent functions that
work with integers, it can also be thought of as containing
internal/core functions that are needed by the classes of the core.
"""

from ..external.gmpy import (gcdext)

def igcdex(a, b):
    """Returns x, y, g such that g = x*a + y*b = gcd(a, b).

    Examples
    ========

    >>> from sympy.core.intfunc import igcdex
    >>> igcdex(2, 3)
    (-1, 1, 1)
    >>> igcdex(10, 12)
    (-1, 1, 2)

    >>> x, y, g = igcdex(100, 2004)
    >>> x, y, g
    (-20, 1, 4)
    >>> x*100 + y*2004
    4

    """
    if (not a) and (not b):
        return (0, 1, 0)
    g, x, y = gcdext(int(a), int(b))
    return x, y, g

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/sympy/core/intfunc.py`.

**Functions defined**: igcdex

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 28
- Comment lines: 4
- Blank lines: 4

### Main Components

**Functions** (1):
- `igcdex()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `intfunc` (imported)



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/sympy/core/intfunc.py
```

