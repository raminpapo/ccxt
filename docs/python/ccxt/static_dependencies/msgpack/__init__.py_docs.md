# Documentation: python/ccxt/static_dependencies/msgpack/__init__.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/msgpack/__init__.py`
- **Size**: 1,077 bytes
- **Lines**: 56
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from .exceptions import *
from .ext import ExtType, Timestamp

import os


version = (1, 0, 7)
__version__ = "1.0.7"


if os.environ.get("MSGPACK_PUREPYTHON"):
    from .fallback import Packer, unpackb, Unpacker
else:
    try:
        from ._cmsgpack import Packer, unpackb, Unpacker
    except ImportError:
        from .fallback import Packer, unpackb, Unpacker


def pack(o, stream, **kwargs):
    """
    Pack object `o` and write it to `stream`

    See :class:`Packer` for options.
    """
    packer = Packer(**kwargs)
    stream.write(packer.pack(o))


def packb(o, **kwargs):
    """
    Pack object `o` and return packed bytes

    See :class:`Packer` for options.
    """
    return Packer(**kwargs).pack(o)


def unpack(stream, **kwargs):
    """
    Unpack an object from `stream`.

    Raises `ExtraData` when `stream` contains extra bytes.
    See :class:`Unpacker` for options.
    """
    data = stream.read()
    return unpackb(data, **kwargs)


# alias for compatibility to simplejson/marshal/pickle.
load = unpack
loads = unpackb

dump = pack
dumps = packb

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/msgpack/__init__.py`.

**Functions defined**: packb, pack, unpack

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 37
- Comment lines: 7
- Blank lines: 12

### Main Components

**Functions** (3):
- `pack()`
- `packb()`
- `unpack()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/msgpack/__init__.py
```

