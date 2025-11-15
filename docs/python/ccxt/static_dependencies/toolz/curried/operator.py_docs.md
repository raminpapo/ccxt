# Documentation: python/ccxt/static_dependencies/toolz/curried/operator.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/toolz/curried/operator.py`
- **Size**: 525 bytes
- **Lines**: 23
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from __future__ import absolute_import

import operator

from ..functoolz import curry


# Tests will catch if/when this needs updated
IGNORE = {
    "__abs__", "__index__", "__inv__", "__invert__", "__neg__", "__not__",
    "__pos__", "_abs", "abs", "attrgetter", "index", "inv", "invert",
    "itemgetter", "neg", "not_", "pos", "truth"
}
locals().update(
    {name: f if name in IGNORE else curry(f)
     for name, f in vars(operator).items() if callable(f)}
)

# Clean up the namespace.
del IGNORE
del curry
del operator

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/toolz/curried/operator.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 15
- Comment lines: 2
- Blank lines: 6

### Main Components

**Constants** (1):
- `IGNORE`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/toolz/curried/operator.py
```

