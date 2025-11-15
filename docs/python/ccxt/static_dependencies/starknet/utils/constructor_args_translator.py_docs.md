# Documentation: python/ccxt/static_dependencies/starknet/utils/constructor_args_translator.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/utils/constructor_args_translator.py`
- **Size**: 2,537 bytes
- **Lines**: 87
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from typing import List, Optional, Union

from ..abi.v2 import shape as ShapeV2
from ..abi.v0 import AbiParser as AbiParserV0
from ..abi.v1 import AbiParser as AbiParserV1
from ..abi.v2 import AbiParser as AbiParserV2
from ..serialization import (
    FunctionSerializationAdapter,
    serializer_for_function,
)
from ..serialization.factory import (
    serializer_for_constructor_v2,
    serializer_for_function_v1,
)


def translate_constructor_args(
    abi: List, constructor_args: Optional[Union[List, dict]], *, cairo_version: int = 1
) -> List[int]:
    serializer = (
        _get_constructor_serializer_v1(abi)
        if cairo_version == 1
        else _get_constructor_serializer_v0(abi)
    )

    if serializer is None or len(serializer.inputs_serializer.serializers) == 0:
        return []

    if not constructor_args:
        raise ValueError(
            "Provided contract has a constructor and no arguments were provided."
        )

    args, kwargs = (
        ([], constructor_args)
        if isinstance(constructor_args, dict)
        else (constructor_args, {})
    )
    return serializer.serialize(*args, **kwargs)


def _get_constructor_serializer_v1(abi: List) -> Optional[FunctionSerializationAdapter]:
    if _is_abi_v2(abi):
        parsed = AbiParserV2(abi).parse()
        constructor = parsed.constructor

        if constructor is None or not constructor.inputs:
            return None

        return serializer_for_constructor_v2(constructor)

    parsed = AbiParserV1(abi).parse()
    constructor = parsed.functions.get("constructor", None)

    # Constructor might not accept any arguments
    if constructor is None or not constructor.inputs:
        return None

    return serializer_for_function_v1(constructor)


def _is_abi_v2(abi: List) -> bool:
    for entry in abi:
        if entry["type"] in [
            ShapeV2.CONSTRUCTOR_ENTRY,
            ShapeV2.L1_HANDLER_ENTRY,
            ShapeV2.INTERFACE_ENTRY,
            ShapeV2.IMPL_ENTRY,
        ]:
            return True
        if entry["type"] == ShapeV2.EVENT_ENTRY:
            if "inputs" in entry:
                return False
            if "kind" in entry:
                return True
    return False


def _get_constructor_serializer_v0(abi: List) -> Optional[FunctionSerializationAdapter]:
    parsed = AbiParserV0(abi).parse()

    # Constructor might not accept any arguments
    if not parsed.constructor or not parsed.constructor.inputs:
        return None

    return serializer_for_function(parsed.constructor)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/utils/constructor_args_translator.py`.

**Functions defined**: _is_abi_v2, _get_constructor_serializer_v0, translate_constructor_args, _get_constructor_serializer_v1

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 87
- Code lines: 65
- Comment lines: 2
- Blank lines: 20

### Main Components

**Functions** (4):
- `_get_constructor_serializer_v0()`
- `_get_constructor_serializer_v1()`
- `_is_abi_v2()`
- `translate_constructor_args()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/utils/constructor_args_translator.py
```

