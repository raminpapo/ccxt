# Documentation: python/ccxt/static_dependencies/lark/common.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/lark/common.py`
- **Size**: 3,008 bytes
- **Lines**: 87
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from copy import deepcopy
import sys
from types import ModuleType
from typing import Callable, Collection, Dict, Optional, TYPE_CHECKING, List

if TYPE_CHECKING:
    from .lark import PostLex
    from .lexer import Lexer
    from .grammar import Rule
    from typing import Union, Type
    from typing import Literal
    if sys.version_info >= (3, 10):
        from typing import TypeAlias
    else:
        from typing_extensions import TypeAlias

from .utils import Serialize
from .lexer import TerminalDef, Token

###{standalone

_ParserArgType: 'TypeAlias' = 'Literal["earley", "lalr", "cyk", "auto"]'
_LexerArgType: 'TypeAlias' = 'Union[Literal["auto", "basic", "contextual", "dynamic", "dynamic_complete"], Type[Lexer]]'
_LexerCallback = Callable[[Token], Token]
ParserCallbacks = Dict[str, Callable]

class LexerConf(Serialize):
    __serialize_fields__ = 'terminals', 'ignore', 'g_regex_flags', 'use_bytes', 'lexer_type'
    __serialize_namespace__ = TerminalDef,

    terminals: Collection[TerminalDef]
    re_module: ModuleType
    ignore: Collection[str]
    postlex: 'Optional[PostLex]'
    callbacks: Dict[str, _LexerCallback]
    g_regex_flags: int
    skip_validation: bool
    use_bytes: bool
    lexer_type: Optional[_LexerArgType]
    strict: bool

    def __init__(self, terminals: Collection[TerminalDef], re_module: ModuleType, ignore: Collection[str]=(), postlex: 'Optional[PostLex]'=None,
                 callbacks: Optional[Dict[str, _LexerCallback]]=None, g_regex_flags: int=0, skip_validation: bool=False, use_bytes: bool=False, strict: bool=False):
        self.terminals = terminals
        self.terminals_by_name = {t.name: t for t in self.terminals}
        assert len(self.terminals) == len(self.terminals_by_name)
        self.ignore = ignore
        self.postlex = postlex
        self.callbacks = callbacks or {}
        self.g_regex_flags = g_regex_flags
        self.re_module = re_module
        self.skip_validation = skip_validation
        self.use_bytes = use_bytes
        self.strict = strict
        self.lexer_type = None

    def _deserialize(self):
        self.terminals_by_name = {t.name: t for t in self.terminals}

    def __deepcopy__(self, memo=None):
        return type(self)(
            deepcopy(self.terminals, memo),
            self.re_module,
            deepcopy(self.ignore, memo),
            deepcopy(self.postlex, memo),
            deepcopy(self.callbacks, memo),
            deepcopy(self.g_regex_flags, memo),
            deepcopy(self.skip_validation, memo),
            deepcopy(self.use_bytes, memo),
        )

class ParserConf(Serialize):
    __serialize_fields__ = 'rules', 'start', 'parser_type'

    rules: List['Rule']
    callbacks: ParserCallbacks
    start: List[str]
    parser_type: _ParserArgType

    def __init__(self, rules: List['Rule'], callbacks: ParserCallbacks, start: List[str]):
        assert isinstance(start, list)
        self.rules = rules
        self.callbacks = callbacks
        self.start = start

###}

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/lark/common.py`.

**Classes defined**: LexerConf, ParserConf

**Functions defined**: __init__, __deepcopy__, _deserialize

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 87
- Code lines: 71
- Comment lines: 2
- Blank lines: 14

### Main Components

**Classes** (2):
- `LexerConf`
- `ParserConf`

**Functions** (3):
- `__deepcopy__()`
- `__init__()`
- `_deserialize()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/lark/common.py
```

