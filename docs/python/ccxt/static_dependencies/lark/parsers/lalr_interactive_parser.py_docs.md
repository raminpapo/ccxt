# Documentation: python/ccxt/static_dependencies/lark/parsers/lalr_interactive_parser.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/lark/parsers/lalr_interactive_parser.py`
- **Size**: 5,751 bytes
- **Lines**: 159
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# This module provides a LALR interactive parser, which is used for debugging and error handling

from typing import Iterator, List
from copy import copy
import warnings

from ..exceptions import UnexpectedToken
from ..lexer import Token, LexerThread
from .lalr_parser_state import ParserState

###{standalone

class InteractiveParser:
    """InteractiveParser gives you advanced control over parsing and error handling when parsing with LALR.

    For a simpler interface, see the ``on_error`` argument to ``Lark.parse()``.
    """
    def __init__(self, parser, parser_state: ParserState, lexer_thread: LexerThread):
        self.parser = parser
        self.parser_state = parser_state
        self.lexer_thread = lexer_thread
        self.result = None

    @property
    def lexer_state(self) -> LexerThread:
        warnings.warn("lexer_state will be removed in subsequent releases. Use lexer_thread instead.", DeprecationWarning)
        return self.lexer_thread

    def feed_token(self, token: Token):
        """Feed the parser with a token, and advance it to the next state, as if it received it from the lexer.

        Note that ``token`` has to be an instance of ``Token``.
        """
        return self.parser_state.feed_token(token, token.type == '$END')

    def iter_parse(self) -> Iterator[Token]:
        """Step through the different stages of the parse, by reading tokens from the lexer
        and feeding them to the parser, one per iteration.

        Returns an iterator of the tokens it encounters.

        When the parse is over, the resulting tree can be found in ``InteractiveParser.result``.
        """
        for token in self.lexer_thread.lex(self.parser_state):
            yield token
            self.result = self.feed_token(token)

    def exhaust_lexer(self) -> List[Token]:
        """Try to feed the rest of the lexer state into the interactive parser.

        Note that this modifies the instance in place and does not feed an '$END' Token
        """
        return list(self.iter_parse())


    def feed_eof(self, last_token=None):
        """Feed a '$END' Token. Borrows from 'last_token' if given."""
        eof = Token.new_borrow_pos('$END', '', last_token) if last_token is not None else self.lexer_thread._Token('$END', '', 0, 1, 1)
        return self.feed_token(eof)


    def __copy__(self):
        """Create a new interactive parser with a separate state.

        Calls to feed_token() won't affect the old instance, and vice-versa.
        """
        return self.copy()

    def copy(self, deepcopy_values=True):
        return type(self)(
            self.parser,
            self.parser_state.copy(deepcopy_values=deepcopy_values),
            copy(self.lexer_thread),
        )

    def __eq__(self, other):
        if not isinstance(other, InteractiveParser):
            return False

        return self.parser_state == other.parser_state and self.lexer_thread == other.lexer_thread

    def as_immutable(self):
        """Convert to an ``ImmutableInteractiveParser``."""
        p = copy(self)
        return ImmutableInteractiveParser(p.parser, p.parser_state, p.lexer_thread)

    def pretty(self):
        """Print the output of ``choices()`` in a way that's easier to read."""
        out = ["Parser choices:"]
        for k, v in self.choices().items():
            out.append('\t- %s -> %r' % (k, v))
        out.append('stack size: %s' % len(self.parser_state.state_stack))
        return '\n'.join(out)

    def choices(self):
        """Returns a dictionary of token types, matched to their action in the parser.

        Only returns token types that are accepted by the current state.

        Updated by ``feed_token()``.
        """
        return self.parser_state.parse_conf.parse_table.states[self.parser_state.position]

    def accepts(self):
        """Returns the set of possible tokens that will advance the parser into a new valid state."""
        accepts = set()
        conf_no_callbacks = copy(self.parser_state.parse_conf)
        # We don't want to call callbacks here since those might have arbitrary side effects
        # and are unnecessarily slow.
        conf_no_callbacks.callbacks = {}
        for t in self.choices():
            if t.isupper(): # is terminal?
                new_cursor = self.copy(deepcopy_values=False)
                new_cursor.parser_state.parse_conf = conf_no_callbacks
                try:
                    new_cursor.feed_token(self.lexer_thread._Token(t, ''))
                except UnexpectedToken:
                    pass
                else:
                    accepts.add(t)
        return accepts

    def resume_parse(self):
        """Resume automated parsing from the current state.
        """
        return self.parser.parse_from_state(self.parser_state, last_token=self.lexer_thread.state.last_token)



class ImmutableInteractiveParser(InteractiveParser):
    """Same as ``InteractiveParser``, but operations create a new instance instead
    of changing it in-place.
    """

    result = None

    def __hash__(self):
        return hash((self.parser_state, self.lexer_thread))

    def feed_token(self, token):
        c = copy(self)
        c.result = InteractiveParser.feed_token(c, token)
        return c

    def exhaust_lexer(self):
        """Try to feed the rest of the lexer state into the parser.

        Note that this returns a new ImmutableInteractiveParser and does not feed an '$END' Token"""
        cursor = self.as_mutable()
        cursor.exhaust_lexer()
        return cursor.as_immutable()

    def as_mutable(self):
        """Convert to an ``InteractiveParser``."""
        p = copy(self)
        return InteractiveParser(p.parser, p.parser_state, p.lexer_thread)

###}

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/lark/parsers/lalr_interactive_parser.py`.

**Classes defined**: ImmutableInteractiveParser, InteractiveParser

**Functions defined**: exhaust_lexer, feed_token, copy, feed_eof, __init__, as_immutable, iter_parse, lexer_state, __eq__, __copy__

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 159
- Code lines: 115
- Comment lines: 27
- Blank lines: 17

### Main Components

**Classes** (2):
- `ImmutableInteractiveParser`
- `InteractiveParser`

**Functions** (16):
- `__copy__()`
- `__eq__()`
- `__hash__()`
- `__init__()`
- `accepts()`
- `as_immutable()`
- `as_mutable()`
- `choices()`
- `copy()`
- `exhaust_lexer()`
- `feed_eof()`
- `feed_token()`
- `iter_parse()`
- `lexer_state()`
- `pretty()`
- `resume_parse()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `last_token` (imported)



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/lark/parsers/lalr_interactive_parser.py
```

