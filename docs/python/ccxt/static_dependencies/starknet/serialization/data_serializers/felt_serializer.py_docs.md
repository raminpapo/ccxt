# Documentation: python/ccxt/static_dependencies/starknet/serialization/data_serializers/felt_serializer.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/serialization/data_serializers/felt_serializer.py`
- **Size**: 1,548 bytes
- **Lines**: 51
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import warnings
from dataclasses import dataclass
from typing import Generator

from ...cairo.felt import encode_shortstring, is_in_felt_range
from ...constants import FIELD_PRIME
from .._context import (
    Context,
    DeserializationContext,
    SerializationContext,
)
from .cairo_data_serializer import (
    CairoDataSerializer,
)


@dataclass
class FeltSerializer(CairoDataSerializer[int, int]):
    """
    Serializer for field element. At the time of writing it is the only existing numeric type.
    """

    def deserialize_with_context(self, context: DeserializationContext) -> int:
        [val] = context.reader.read(1)
        self._ensure_felt(context, val)
        return val

    def serialize_with_context(
        self, context: SerializationContext, value: int
    ) -> Generator[int, None, None]:
        if isinstance(value, str):
            warnings.warn(
                "Serializing shortstrings in FeltSerializer is deprecated. "
                "Use starknet_py.cairo.felt.encode_shortstring instead.",
                category=DeprecationWarning,
            )
            value = encode_shortstring(value)
            yield value
            return

        context.ensure_valid_type(value, isinstance(value, int), "int")
        self._ensure_felt(context, value)
        yield value

    @staticmethod
    def _ensure_felt(context: Context, value: int):
        context.ensure_valid_value(
            is_in_felt_range(value),
            f"invalid value '{value}' - must be in [0, {FIELD_PRIME}) range",
        )

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/serialization/data_serializers/felt_serializer.py`.

**Classes defined**: FeltSerializer

**Functions defined**: _ensure_felt, serialize_with_context, deserialize_with_context

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 51
- Code lines: 43
- Comment lines: 2
- Blank lines: 6

### Main Components

**Classes** (1):
- `FeltSerializer`

**Functions** (3):
- `_ensure_felt()`
- `deserialize_with_context()`
- `serialize_with_context()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/serialization/data_serializers/felt_serializer.py
```

