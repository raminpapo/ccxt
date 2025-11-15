# Documentation: python/ccxt/static_dependencies/marshmallow/error_store.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/marshmallow/error_store.py`
- **Size**: 2,212 bytes
- **Lines**: 61
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
"""Utilities for storing collections of error messages.

.. warning::

    This module is treated as private API.
    Users should not need to use this module directly.
"""

from .exceptions import SCHEMA


class ErrorStore:
    def __init__(self):
        #: Dictionary of errors stored during serialization
        self.errors = {}

    def store_error(self, messages, field_name=SCHEMA, index=None):
        # field error  -> store/merge error messages under field name key
        # schema error -> if string or list, store/merge under _schema key
        #              -> if dict, store/merge with other top-level keys
        if field_name != SCHEMA or not isinstance(messages, dict):
            messages = {field_name: messages}
        if index is not None:
            messages = {index: messages}
        self.errors = merge_errors(self.errors, messages)


def merge_errors(errors1, errors2):
    """Deeply merge two error messages.

    The format of ``errors1`` and ``errors2`` matches the ``message``
    parameter of :exc:`marshmallow.exceptions.ValidationError`.
    """
    if not errors1:
        return errors2
    if not errors2:
        return errors1
    if isinstance(errors1, list):
        if isinstance(errors2, list):
            return errors1 + errors2
        if isinstance(errors2, dict):
            return dict(errors2, **{SCHEMA: merge_errors(errors1, errors2.get(SCHEMA))})
        return errors1 + [errors2]
    if isinstance(errors1, dict):
        if isinstance(errors2, list):
            return dict(errors1, **{SCHEMA: merge_errors(errors1.get(SCHEMA), errors2)})
        if isinstance(errors2, dict):
            errors = dict(errors1)
            for key, val in errors2.items():
                if key in errors:
                    errors[key] = merge_errors(errors[key], val)
                else:
                    errors[key] = val
            return errors
        return dict(errors1, **{SCHEMA: merge_errors(errors1.get(SCHEMA), errors2)})
    if isinstance(errors2, list):
        return [errors1] + errors2
    if isinstance(errors2, dict):
        return dict(errors2, **{SCHEMA: merge_errors(errors1, errors2.get(SCHEMA))})
    return [errors1, errors2]

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/marshmallow/error_store.py`.

**Classes defined**: ErrorStore

**Functions defined**: store_error, __init__, merge_errors

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 47
- Comment lines: 8
- Blank lines: 6

### Main Components

**Classes** (1):
- `ErrorStore`

**Functions** (3):
- `__init__()`
- `merge_errors()`
- `store_error()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/marshmallow/error_store.py
```

