# Documentation: python/ccxt/static_dependencies/starknet/abi/v2/shape.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/abi/v2/shape.py`
- **Size**: 2,043 bytes
- **Lines**: 108
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from __future__ import annotations

from typing import List, Literal, Optional, TypedDict, Union

STRUCT_ENTRY = "struct"
EVENT_ENTRY = "event"
FUNCTION_ENTRY = "function"
ENUM_ENTRY = "enum"
CONSTRUCTOR_ENTRY = "constructor"
L1_HANDLER_ENTRY = "l1_handler"
IMPL_ENTRY = "impl"
INTERFACE_ENTRY = "interface"

DATA_KIND = "data"
NESTED_KIND = "nested"


class TypeDict(TypedDict):
    type: str


class TypedParameterDict(TypeDict):
    name: str


class StructDict(TypedDict):
    type: Literal["struct"]
    name: str
    members: List[TypedParameterDict]


class FunctionBaseDict(TypedDict):
    name: str
    inputs: List[TypedParameterDict]
    outputs: List[TypeDict]
    state_mutability: Optional[Literal["external", "view"]]


class FunctionDict(FunctionBaseDict):
    type: Literal["function"]


class ConstructorDict(TypedDict):
    type: Literal["constructor"]
    name: str
    inputs: List[TypedParameterDict]


class L1HandlerDict(FunctionBaseDict):
    type: Literal["l1_handler"]


class EventBaseDict(TypedDict):
    type: Literal["event"]
    name: str


class EventStructMemberDict(TypedParameterDict):
    kind: Literal["data"]


class EventStructDict(EventBaseDict):
    kind: Literal["struct"]
    members: List[EventStructMemberDict]


class EventEnumVariantDict(TypedParameterDict):
    kind: Literal["nested"]


class EventEnumDict(EventBaseDict):
    kind: Literal["enum"]
    variants: List[EventEnumVariantDict]


EventDict = Union[EventStructDict, EventEnumDict]


class EnumDict(TypedDict):
    type: Literal["enum"]
    name: str
    variants: List[TypedParameterDict]


class ImplDict(TypedDict):
    type: Literal["impl"]
    name: str
    interface_name: str


class InterfaceDict(TypedDict):
    type: Literal["interface"]
    name: str
    items: List[FunctionDict]  # for now only functions can be defined here


AbiDictEntry = Union[
    StructDict,
    FunctionDict,
    EventDict,
    EnumDict,
    ConstructorDict,
    L1HandlerDict,
    ImplDict,
    InterfaceDict,
]
AbiDictList = List[AbiDictEntry]

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/abi/v2/shape.py`.

**Classes defined**: FunctionBaseDict, TypedParameterDict, TypeDict, StructDict, EventStructDict, FunctionDict, EventBaseDict, L1HandlerDict, EventStructMemberDict, ConstructorDict

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 108
- Code lines: 70
- Comment lines: 0
- Blank lines: 38

### Main Components

**Classes** (15):
- `ConstructorDict`
- `EnumDict`
- `EventBaseDict`
- `EventEnumDict`
- `EventEnumVariantDict`
- `EventStructDict`
- `EventStructMemberDict`
- `FunctionBaseDict`
- `FunctionDict`
- `ImplDict`
- `InterfaceDict`
- `L1HandlerDict`
- `StructDict`
- `TypeDict`
- `TypedParameterDict`

**Constants** (10):
- `CONSTRUCTOR_ENTRY`
- `DATA_KIND`
- `ENUM_ENTRY`
- `EVENT_ENTRY`
- `FUNCTION_ENTRY`
- `IMPL_ENTRY`
- `INTERFACE_ENTRY`
- `L1_HANDLER_ENTRY`
- `NESTED_KIND`
- `STRUCT_ENTRY`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/abi/v2/shape.py
```

