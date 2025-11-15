# Documentation: python/ccxt/static_dependencies/toolz/compatibility.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/toolz/compatibility.py`
- **Size**: 997 bytes
- **Lines**: 31
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import warnings
warnings.warn("The toolz.compatibility module is no longer "
              "needed in Python 3 and has been deprecated. Please "
              "import these utilities directly from the standard library. "
              "This module will be removed in a future release.",
              category=DeprecationWarning, stacklevel=2)

import operator
import sys

PY3 = sys.version_info[0] > 2
PY34 = sys.version_info[0] == 3 and sys.version_info[1] == 4
PYPY = hasattr(sys, 'pypy_version_info') and PY3

__all__ = ('map', 'filter', 'range', 'zip', 'reduce', 'zip_longest',
           'iteritems', 'iterkeys', 'itervalues', 'filterfalse',
           'PY3', 'PY34', 'PYPY')


map = map
filter = filter
range = range
zip = zip
from functools import reduce
from itertools import zip_longest
from itertools import filterfalse
iteritems = operator.methodcaller('items')
iterkeys = operator.methodcaller('keys')
itervalues = operator.methodcaller('values')
from collections.abc import Sequence

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/toolz/compatibility.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 25
- Comment lines: 0
- Blank lines: 6

### Main Components

**Constants** (3):
- `PY3`
- `PY34`
- `PYPY`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `
              ` (imported)



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/toolz/compatibility.py
```

