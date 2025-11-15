# Documentation: python/ccxt/static_dependencies/marshmallow_dataclass/mypy.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/marshmallow_dataclass/mypy.py`
- **Size**: 2,034 bytes
- **Lines**: 72
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import inspect
from typing import Callable, Optional, Type

from mypy import nodes
from mypy.plugin import DynamicClassDefContext, Plugin
from mypy.plugins import dataclasses

import marshmallow_dataclass

_NEW_TYPE_SIG = inspect.signature(marshmallow_dataclass.NewType)


def plugin(version: str) -> Type[Plugin]:
    return MarshmallowDataclassPlugin


class MarshmallowDataclassPlugin(Plugin):
    def get_dynamic_class_hook(
        self, fullname: str
    ) -> Optional[Callable[[DynamicClassDefContext], None]]:
        if fullname == "marshmallow_dataclass.NewType":
            return new_type_hook
        return None

    def get_class_decorator_hook(self, fullname: str):
        if fullname == "marshmallow_dataclass.dataclass":
            return dataclasses.dataclass_class_maker_callback
        return None


def new_type_hook(ctx: DynamicClassDefContext) -> None:
    """
    Dynamic class hook for :func:`marshmallow_dataclass.NewType`.

    Uses the type of the ``typ`` argument.
    """
    typ = _get_arg_by_name(ctx.call, "typ", _NEW_TYPE_SIG)
    if not isinstance(typ, nodes.RefExpr):
        return
    info = typ.node
    if not isinstance(info, nodes.TypeInfo):
        return
    ctx.api.add_symbol_table_node(ctx.name, nodes.SymbolTableNode(nodes.GDEF, info))


def _get_arg_by_name(
    call: nodes.CallExpr, name: str, sig: inspect.Signature
) -> Optional[nodes.Expression]:
    """
    Get value of argument from a call.

    :return: The argument value, or ``None`` if it cannot be found.

    .. warning::
        This probably doesn't yet work for calls with ``*args`` and/or ``*kwargs``.
    """
    args = []
    kwargs = {}
    for arg_name, arg_value in zip(call.arg_names, call.args):
        if arg_name is None:
            args.append(arg_value)
        else:
            kwargs[arg_name] = arg_value
    try:
        bound_args = sig.bind(*args, **kwargs)
    except TypeError:
        return None
    try:
        return bound_args.arguments[name]
    except KeyError:
        return None

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/marshmallow_dataclass/mypy.py`.

**Classes defined**: MarshmallowDataclassPlugin, hook

**Functions defined**: new_type_hook, plugin, get_dynamic_class_hook, get_class_decorator_hook, _get_arg_by_name

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 72
- Code lines: 56
- Comment lines: 4
- Blank lines: 12

### Main Components

**Classes** (1):
- `MarshmallowDataclassPlugin`

**Functions** (5):
- `_get_arg_by_name()`
- `get_class_decorator_hook()`
- `get_dynamic_class_hook()`
- `new_type_hook()`
- `plugin()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/marshmallow_dataclass/mypy.py
```

