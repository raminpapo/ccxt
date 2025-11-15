# Documentation: python/ccxt/static_dependencies/starknet/cairo/deprecated_parse/parser.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/cairo/deprecated_parse/parser.py`
- **Size**: 1,280 bytes
- **Lines**: 47
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ....lark import Lark

from .cairo_types import CairoType
from .parser_transformer import ParserTransformer

CAIRO_EBNF = """
    %import common.WS_INLINE
    %ignore WS_INLINE

    IDENTIFIER: /[a-zA-Z_][a-zA-Z_0-9]*/
    _DBL_STAR: "**"
    COMMA: ","

    ?type: non_identifier_type
        | identifier             -> type_struct

    comma_separated{item}: item? (COMMA item)* COMMA?

    named_type: identifier (":" type)? | non_identifier_type
    non_identifier_type: "felt"                                         -> type_felt
                    | "codeoffset"                                   -> type_codeoffset
                    | type "*"                                       -> type_pointer
                    | type _DBL_STAR                                 -> type_pointer2
                    | "(" comma_separated{named_type} ")" -> type_tuple

    identifier: IDENTIFIER ("." IDENTIFIER)*
"""


def parse(code: str) -> CairoType:
    """
    Parses the given string and returns a CairoType.
    """

    grammar = CAIRO_EBNF

    grammar_parser = Lark(
        grammar=grammar,
        start=["type"],
        parser="lalr",
    )

    parsed = grammar_parser.parse(code)
    transformed = ParserTransformer().transform(parsed)

    return transformed

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/cairo/deprecated_parse/parser.py`.

**Functions defined**: parse

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 33
- Comment lines: 3
- Blank lines: 11

### Main Components

**Functions** (1):
- `parse()`

**Constants** (1):
- `CAIRO_EBNF`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/cairo/deprecated_parse/parser.py
```

