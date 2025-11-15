# Documentation: python/ccxt/static_dependencies/starknet/serialization/data_serializers/option_serializer.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/serialization/data_serializers/option_serializer.py`
- **Size**: 1,136 bytes
- **Lines**: 44
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
class OptionSerializer(CairoDataSerializer[Optional[Any], Optional[Any]]):
    """
    Serializer for Option type.
    Can serialize None and common CairoTypes.
    Deserializes data to None or CairoType.

    Example:
        None => [1]
        {"option1": 123, "option2": None} => [0, 123, 1]
    """

    serializer: CairoDataSerializer

    def deserialize_with_context(
        self, context: DeserializationContext
    ) -> Optional[Any]:
        (is_none,) = context.reader.read(1)
        if is_none == 1:
            return None

        return self.serializer.deserialize_with_context(context)

    def serialize_with_context(
        self, context: SerializationContext, value: Optional[Any]
    ) -> Generator[int, None, None]:
        if value is None:
            yield 1
        else:
            yield 0
            yield from self.serializer.serialize_with_context(context, value)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/serialization/data_serializers/option_serializer.py`.

**Classes defined**: OptionSerializer

**Functions defined**: serialize_with_context, deserialize_with_context

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 35
- Comment lines: 2
- Blank lines: 7

### Main Components

**Classes** (1):
- `OptionSerializer`

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
python python/ccxt/static_dependencies/starknet/serialization/data_serializers/option_serializer.py
```

