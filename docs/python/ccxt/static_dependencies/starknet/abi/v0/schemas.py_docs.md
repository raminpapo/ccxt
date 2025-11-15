# Documentation: python/ccxt/static_dependencies/starknet/abi/v0/schemas.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/abi/v0/schemas.py`
- **Size**: 2,254 bytes
- **Lines**: 73
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ....marshmallow import Schema, fields
from ....marshmallow_oneofschema import OneOfSchema

from .shape import (
    CONSTRUCTOR_ENTRY,
    EVENT_ENTRY,
    FUNCTION_ENTRY,
    L1_HANDLER_ENTRY,
    STRUCT_ENTRY,
)


class TypedParameterSchema(Schema):
    name = fields.String(data_key="name", required=True)
    type = fields.String(data_key="type", required=True)


class StructMemberSchema(TypedParameterSchema):
    offset = fields.Integer(data_key="offset", required=False)


class FunctionBaseSchema(Schema):
    name = fields.String(data_key="name", required=True)
    inputs = fields.List(
        fields.Nested(TypedParameterSchema()), data_key="inputs", required=True
    )
    outputs = fields.List(
        fields.Nested(TypedParameterSchema()), data_key="outputs", required=True
    )


class FunctionAbiEntrySchema(FunctionBaseSchema):
    type = fields.Constant(FUNCTION_ENTRY, data_key="type", required=True)


class ConstructorAbiEntrySchema(FunctionBaseSchema):
    type = fields.Constant(CONSTRUCTOR_ENTRY, data_key="type", required=True)


class L1HandlerAbiEntrySchema(FunctionBaseSchema):
    type = fields.Constant(L1_HANDLER_ENTRY, data_key="type", required=True)


class EventAbiEntrySchema(Schema):
    type = fields.Constant(EVENT_ENTRY, data_key="type", required=True)
    name = fields.String(data_key="name", required=True)
    keys = fields.List(
        fields.Nested(TypedParameterSchema()), data_key="keys", required=True
    )
    data = fields.List(
        fields.Nested(TypedParameterSchema()), data_key="data", required=True
    )


class StructAbiEntrySchema(Schema):
    type = fields.Constant(STRUCT_ENTRY, data_key="type", required=True)
    name = fields.String(data_key="name", required=True)
    size = fields.Integer(data_key="size", required=True)
    members = fields.List(
        fields.Nested(StructMemberSchema()), data_key="members", required=True
    )


class ContractAbiEntrySchema(OneOfSchema):
    type_field_remove = False
    type_schemas = {
        FUNCTION_ENTRY: FunctionAbiEntrySchema,
        L1_HANDLER_ENTRY: L1HandlerAbiEntrySchema,
        CONSTRUCTOR_ENTRY: ConstructorAbiEntrySchema,
        EVENT_ENTRY: EventAbiEntrySchema,
        STRUCT_ENTRY: StructAbiEntrySchema,
    }

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/abi/v0/schemas.py`.

**Classes defined**: L1HandlerAbiEntrySchema, TypedParameterSchema, FunctionAbiEntrySchema, StructMemberSchema, EventAbiEntrySchema, ConstructorAbiEntrySchema, StructAbiEntrySchema, ContractAbiEntrySchema, FunctionBaseSchema

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 73
- Code lines: 53
- Comment lines: 0
- Blank lines: 20

### Main Components

**Classes** (9):
- `ConstructorAbiEntrySchema`
- `ContractAbiEntrySchema`
- `EventAbiEntrySchema`
- `FunctionAbiEntrySchema`
- `FunctionBaseSchema`
- `L1HandlerAbiEntrySchema`
- `StructAbiEntrySchema`
- `StructMemberSchema`
- `TypedParameterSchema`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/abi/v0/schemas.py
```

