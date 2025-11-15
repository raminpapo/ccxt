# Documentation: python/ccxt/static_dependencies/lark/parsers/earley_common.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/lark/parsers/earley_common.py`
- **Size**: 1,620 bytes
- **Lines**: 43
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
"""This module implements useful building blocks for the Earley parser
"""


class Item:
    "An Earley Item, the atom of the algorithm."

    __slots__ = ('s', 'rule', 'ptr', 'start', 'is_complete', 'expect', 'previous', 'node', '_hash')
    def __init__(self, rule, ptr, start):
        self.is_complete = len(rule.expansion) == ptr
        self.rule = rule    # rule
        self.ptr = ptr      # ptr
        self.start = start  # j
        self.node = None    # w
        if self.is_complete:
            self.s = rule.origin
            self.expect = None
            self.previous = rule.expansion[ptr - 1] if ptr > 0 and len(rule.expansion) else None
        else:
            self.s = (rule, ptr)
            self.expect = rule.expansion[ptr]
            self.previous = rule.expansion[ptr - 1] if ptr > 0 and len(rule.expansion) else None
        self._hash = hash((self.s, self.start, self.rule))

    def advance(self):
        return Item(self.rule, self.ptr + 1, self.start)

    def __eq__(self, other):
        return self is other or (self.s == other.s and self.start == other.start and self.rule == other.rule)

    def __hash__(self):
        return self._hash

    def __repr__(self):
        before = ( expansion.name for expansion in self.rule.expansion[:self.ptr] )
        after = ( expansion.name for expansion in self.rule.expansion[self.ptr:] )
        symbol = "{} ::= {}* {}".format(self.rule.origin.name, ' '.join(before), ' '.join(after))
        return '%s (%d)' % (symbol, self.start)


# class TransitiveItem(Item):
#   ...   # removed at commit 4c1cfb2faf24e8f8bff7112627a00b94d261b420

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/lark/parsers/earley_common.py`.

**Classes defined**: TransitiveItem, Item

**Functions defined**: advance, __init__, __hash__, __eq__, __repr__

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 31
- Comment lines: 4
- Blank lines: 8

### Main Components

**Classes** (2):
- `Item`
- `TransitiveItem`

**Functions** (5):
- `__eq__()`
- `__hash__()`
- `__init__()`
- `__repr__()`
- `advance()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/lark/parsers/earley_common.py
```

