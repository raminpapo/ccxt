# Documentation: python/ccxt/static_dependencies/starknet/serialization/data_serializers/unit_serializer.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/serialization/data_serializers/unit_serializer.py`
- **Size**: 778 bytes
- **Lines**: 33
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from dataclasses import dataclass
from typing import Any, Generator, Optional

from .._context import (
    DeserializationContext,
    SerializationContext,
)
from .cairo_data_serializer import (
    CairoDataSerializer,
)


@dataclass
class UnitSerializer(CairoDataSerializer[None, None]):
    """
    Serializer for unit type.
    Can only serialize None.
    Deserializes data to None.

    Example:
        [] => None
    """

    def deserialize_with_context(self, context: DeserializationContext) -> None:
        return None

    def serialize_with_context(
        self, context: SerializationContext, value: Optional[Any]
    ) -> Generator[None, None, None]:
        if value is not None:
            raise ValueError("Can only serialize `None`.")
        yield None

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/serialization/data_serializers/unit_serializer.py`.

**Classes defined**: UnitSerializer

**Functions defined**: serialize_with_context, deserialize_with_context

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 26
- Comment lines: 2
- Blank lines: 5

### Main Components

**Classes** (1):
- `UnitSerializer`

**Functions** (2):
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
python python/ccxt/static_dependencies/starknet/serialization/data_serializers/unit_serializer.py
```

