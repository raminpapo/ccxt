# Documentation: python/ccxt/static_dependencies/starknet/serialization/data_serializers/bool_serializer.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/serialization/data_serializers/bool_serializer.py`
- **Size**: 999 bytes
- **Lines**: 38
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from dataclasses import dataclass
from typing import Generator

from .._context import (
    Context,
    DeserializationContext,
    SerializationContext,
)
from .cairo_data_serializer import (
    CairoDataSerializer,
)


@dataclass
class BoolSerializer(CairoDataSerializer[bool, int]):
    """
    Serializer for boolean.
    """

    def deserialize_with_context(self, context: DeserializationContext) -> bool:
        [val] = context.reader.read(1)
        self._ensure_bool(context, val)
        return bool(val)

    def serialize_with_context(
        self, context: SerializationContext, value: bool
    ) -> Generator[int, None, None]:
        context.ensure_valid_type(value, isinstance(value, bool), "bool")
        self._ensure_bool(context, value)
        yield int(value)

    @staticmethod
    def _ensure_bool(context: Context, value: int):
        context.ensure_valid_value(
            value in [0, 1],
            f"invalid value '{value}' - must be in [0, 2) range",
        )

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/serialization/data_serializers/bool_serializer.py`.

**Classes defined**: BoolSerializer

**Functions defined**: serialize_with_context, _ensure_bool, deserialize_with_context

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 31
- Comment lines: 2
- Blank lines: 5

### Main Components

**Classes** (1):
- `BoolSerializer`

**Functions** (3):
- `_ensure_bool()`
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
python python/ccxt/static_dependencies/starknet/serialization/data_serializers/bool_serializer.py
```

