# Documentation: python/ccxt/static_dependencies/toolz/recipes.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/toolz/recipes.py`
- **Size**: 1,256 bytes
- **Lines**: 47
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import itertools
from .itertoolz import frequencies, pluck, getter


__all__ = ('countby', 'partitionby')


def countby(key, seq):
    """ Count elements of a collection by a key function

    >>> countby(len, ['cat', 'mouse', 'dog'])
    {3: 2, 5: 1}

    >>> def iseven(x): return x % 2 == 0
    >>> countby(iseven, [1, 2, 3])  # doctest:+SKIP
    {True: 1, False: 2}

    See Also:
        groupby
    """
    if not callable(key):
        key = getter(key)
    return frequencies(map(key, seq))


def partitionby(func, seq):
    """ Partition a sequence according to a function

    Partition `s` into a sequence of lists such that, when traversing
    `s`, every time the output of `func` changes a new list is started
    and that and subsequent items are collected into that list.

    >>> is_space = lambda c: c == " "
    >>> list(partitionby(is_space, "I have space"))
    [('I',), (' ',), ('h', 'a', 'v', 'e'), (' ',), ('s', 'p', 'a', 'c', 'e')]

    >>> is_large = lambda x: x > 10
    >>> list(partitionby(is_large, [1, 2, 1, 99, 88, 33, 99, -1, 5]))
    [(1, 2, 1), (99, 88, 33, 99), (-1, 5)]

    See also:
        partition
        groupby
        itertools.groupby
    """
    return map(tuple, pluck(1, itertools.groupby(seq, key=func)))

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/toolz/recipes.py`.

**Functions defined**: countby, iseven, Partition, partitionby

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 33
- Comment lines: 4
- Blank lines: 10

### Main Components

**Functions** (4):
- `Partition()`
- `countby()`
- `iseven()`
- `partitionby()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/toolz/recipes.py
```

