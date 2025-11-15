# Documentation: python/ccxt/static_dependencies/msgpack/exceptions.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/msgpack/exceptions.py`
- **Size**: 1,081 bytes
- **Lines**: 49
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
class UnpackException(Exception):
    """Base class for some exceptions raised while unpacking.

    NOTE: unpack may raise exception other than subclass of
    UnpackException.  If you want to catch all error, catch
    Exception instead.
    """


class BufferFull(UnpackException):
    pass


class OutOfData(UnpackException):
    pass


class FormatError(ValueError, UnpackException):
    """Invalid msgpack format"""


class StackError(ValueError, UnpackException):
    """Too nested"""


# Deprecated.  Use ValueError instead
UnpackValueError = ValueError


class ExtraData(UnpackValueError):
    """ExtraData is raised when there is trailing data.

    This exception is raised while only one-shot (not streaming)
    unpack.
    """

    def __init__(self, unpacked, extra):
        self.unpacked = unpacked
        self.extra = extra

    def __str__(self):
        return "unpack(b) received extra data."


# Deprecated.  Use Exception instead to catch all exception during packing.
PackException = Exception
PackValueError = ValueError
PackOverflowError = OverflowError

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/msgpack/exceptions.py`.

**Classes defined**: ExtraData, UnpackException, for, OutOfData, FormatError, BufferFull, StackError

**Functions defined**: __init__, __str__

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 49
- Code lines: 28
- Comment lines: 8
- Blank lines: 13

### Main Components

**Classes** (7):
- `BufferFull`
- `ExtraData`
- `FormatError`
- `OutOfData`
- `StackError`
- `UnpackException`
- `of`

**Functions** (2):
- `__init__()`
- `__str__()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/msgpack/exceptions.py
```

