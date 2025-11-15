# Documentation: python/ccxt/static_dependencies/starknet/serialization/data_serializers/_common.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/serialization/data_serializers/_common.py`
- **Size**: 2,859 bytes
- **Lines**: 83
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# We have to use parametrised type from typing
from collections import OrderedDict as _OrderedDict
from typing import Dict, Generator, List, OrderedDict

from .._context import (
    DeserializationContext,
    SerializationContext,
)
from .cairo_data_serializer import (
    CairoDataSerializer,
)

# The actual serialization logic is very similar among all serializers: they either serialize data based on
# position or their name. Having this logic reused adds indirection, but makes sure proper logic is used everywhere.


def deserialize_to_list(
    deserializers: List[CairoDataSerializer], context: DeserializationContext
) -> List:
    """
    Deserializes data from context to list. This logic is used in every sequential type (arrays and tuples).
    """
    result = []

    for index, serializer in enumerate(deserializers):
        with context.push_entity(f"[{index}]"):
            result.append(serializer.deserialize_with_context(context))

    return result


def deserialize_to_dict(
    deserializers: OrderedDict[str, CairoDataSerializer],
    context: DeserializationContext,
) -> OrderedDict:
    """
    Deserializes data from context to dictionary. This logic is used in every type with named fields (structs,
    named tuples and payloads).
    """
    result = _OrderedDict()

    for key, serializer in deserializers.items():
        with context.push_entity(key):
            result[key] = serializer.deserialize_with_context(context)

    return result


def serialize_from_list(
    serializers: List[CairoDataSerializer], context: SerializationContext, values: List
) -> Generator[int, None, None]:
    """
    Serializes data from list. This logic is used in every sequential type (arrays and tuples).
    """
    context.ensure_valid_value(
        len(serializers) == len(values),
        f"expected {len(serializers)} elements, {len(values)} provided",
    )

    for index, (serializer, value) in enumerate(zip(serializers, values)):
        with context.push_entity(f"[{index}]"):
            yield from serializer.serialize_with_context(context, value)


def serialize_from_dict(
    serializers: OrderedDict[str, CairoDataSerializer],
    context: SerializationContext,
    values: Dict,
) -> Generator[int, None, None]:
    """
    Serializes data from dict. This logic is used in every type with named fields (structs, named tuples and payloads).
    """
    excessive_keys = set(values.keys()).difference(serializers.keys())
    context.ensure_valid_value(
        not excessive_keys,
        f"unexpected keys '{','.join(excessive_keys)}' were provided",
    )

    for name, serializer in serializers.items():
        with context.push_entity(name):
            context.ensure_valid_value(name in values, f"key '{name}' is missing")
            yield from serializer.serialize_with_context(context, values[name])

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/serialization/data_serializers/_common.py`.

**Functions defined**: deserialize_to_dict, serialize_from_dict, deserialize_to_list, serialize_from_list

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 83
- Code lines: 63
- Comment lines: 11
- Blank lines: 9

### Main Components

**Functions** (4):
- `deserialize_to_dict()`
- `deserialize_to_list()`
- `serialize_from_dict()`
- `serialize_from_list()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/serialization/data_serializers/_common.py
```

