# Documentation: python/ccxt/static_dependencies/ethereum/abi/exceptions.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/ethereum/abi/exceptions.py`
- **Size**: 2,941 bytes
- **Lines**: 140
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ...parsimonious import (
    ParseError
)


class EncodingError(Exception):
    """
    Base exception for any error that occurs during encoding.
    """

    pass


class EncodingTypeError(EncodingError):
    """
    Raised when trying to encode a python value whose type is not supported for
    the output ABI type.
    """

    pass


class IllegalValue(EncodingError):
    """
    Raised when trying to encode a python value with the correct type but with
    a value that is not considered legal for the output ABI type.

    Example:

    .. code-block:: python

        fixed128x19_encoder(Decimal('NaN'))  # cannot encode NaN

    """

    pass


class ValueOutOfBounds(IllegalValue):
    """
    Raised when trying to encode a python value with the correct type but with
    a value that appears outside the range of valid values for the output ABI
    type.

    Example:

    .. code-block:: python

        ufixed8x1_encoder(Decimal('25.6'))  # out of bounds

    """

    pass


class DecodingError(Exception):
    """
    Base exception for any error that occurs during decoding.
    """

    pass


class InsufficientDataBytes(DecodingError):
    """
    Raised when there are insufficient data to decode a value for a given ABI
    type.
    """

    pass


class NonEmptyPaddingBytes(DecodingError):
    """
    Raised when the padding bytes of an ABI value are malformed.
    """

    pass


class ParseError(ParseError):
    """
    Raised when an ABI type string cannot be parsed.
    """

    def __str__(self):
        return "Parse error at '{}' (column {}) in type string '{}'".format(
            self.text[self.pos : self.pos + 5],
            self.column(),
            self.text,
        )


class ABITypeError(ValueError):
    """
    Raised when a parsed ABI type has inconsistent properties; for example,
    when trying to parse the type string ``'uint7'`` (which has a bit-width
    that is not congruent with zero modulo eight).
    """

    pass


class PredicateMappingError(Exception):
    """
    Raised when an error occurs in a registry's internal mapping.
    """

    pass


class NoEntriesFound(ValueError, PredicateMappingError):
    """
    Raised when no registration is found for a type string in a registry's
    internal mapping.

    .. warning::

        In a future version of ``eth-abi``, this error class will no longer
        inherit from ``ValueError``.
    """

    pass


class MultipleEntriesFound(ValueError, PredicateMappingError):
    """
    Raised when multiple registrations are found for a type string in a
    registry's internal mapping.  This error is non-recoverable and indicates
    that a registry was configured incorrectly.  Registrations are expected to
    cover completely distinct ranges of type strings.

    .. warning::

        In a future version of ``eth-abi``, this error class will no longer
        inherit from ``ValueError``.
    """

    pass

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/ethereum/abi/exceptions.py`.

**Classes defined**: EncodingTypeError, DecodingError, ValueOutOfBounds, ABITypeError, NonEmptyPaddingBytes, ParseError, PredicateMappingError, EncodingError, InsufficientDataBytes, IllegalValue

**Functions defined**: __str__

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 140
- Code lines: 91
- Comment lines: 24
- Blank lines: 25

### Main Components

**Classes** (12):
- `ABITypeError`
- `DecodingError`
- `EncodingError`
- `EncodingTypeError`
- `IllegalValue`
- `InsufficientDataBytes`
- `MultipleEntriesFound`
- `NoEntriesFound`
- `NonEmptyPaddingBytes`
- `ParseError`
- `PredicateMappingError`
- `ValueOutOfBounds`

**Functions** (1):
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
python python/ccxt/static_dependencies/ethereum/abi/exceptions.py
```

