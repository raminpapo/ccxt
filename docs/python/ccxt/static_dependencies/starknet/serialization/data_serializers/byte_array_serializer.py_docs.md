# Documentation: python/ccxt/static_dependencies/starknet/serialization/data_serializers/byte_array_serializer.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/serialization/data_serializers/byte_array_serializer.py`
- **Size**: 2,070 bytes
- **Lines**: 67
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from dataclasses import dataclass
from typing import Generator

from ...cairo.felt import decode_shortstring, encode_shortstring
from .._context import (
    DeserializationContext,
    SerializationContext,
)
from ._common import (
    deserialize_to_list,
    serialize_from_list,
)
from .cairo_data_serializer import (
    CairoDataSerializer,
)
from .felt_serializer import FeltSerializer

BYTES_31_SIZE = 31


@dataclass
class ByteArraySerializer(CairoDataSerializer[str, str]):
    """
    Serializer for ByteArrays. Serializes to and deserializes from str values.

    Examples:
    "" => [0,0,0]
    "hello" => [0,448378203247,5]
    """

    def deserialize_with_context(self, context: DeserializationContext) -> str:
        with context.push_entity("data_array_len"):
            [size] = context.reader.read(1)

        data = deserialize_to_list([FeltSerializer()] * size, context)

        with context.push_entity("pending_word"):
            [pending_word] = context.reader.read(1)

        with context.push_entity("pending_word_len"):
            [pending_word_len] = context.reader.read(1)

        pending_word = decode_shortstring(pending_word)
        context.ensure_valid_value(
            len(pending_word) == pending_word_len,
            f"Invalid length {pending_word_len} for pending word {pending_word}",
        )

        data_joined = "".join(map(decode_shortstring, data))
        return data_joined + pending_word

    def serialize_with_context(
        self, context: SerializationContext, value: str
    ) -> Generator[int, None, None]:
        context.ensure_valid_type(value, isinstance(value, str), "str")
        data = [
            value[i : i + BYTES_31_SIZE] for i in range(0, len(value), BYTES_31_SIZE)
        ]
        pending_word = (
            "" if len(data) == 0 or len(data[-1]) == BYTES_31_SIZE else data.pop(-1)
        )

        yield len(data)
        yield from serialize_from_list([FeltSerializer()] * len(data), context, data)
        yield encode_shortstring(pending_word)
        yield len(pending_word)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/serialization/data_serializers/byte_array_serializer.py`.

**Classes defined**: ByteArraySerializer

**Functions defined**: serialize_with_context, deserialize_with_context

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 67
- Code lines: 53
- Comment lines: 2
- Blank lines: 12

### Main Components

**Classes** (1):
- `ByteArraySerializer`

**Functions** (2):
- `deserialize_with_context()`
- `serialize_with_context()`

**Constants** (1):
- `BYTES_31_SIZE`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/serialization/data_serializers/byte_array_serializer.py
```

