# Documentation: wiki/examples/py/exchanges.md

## File Metadata

- **Path**: `wiki/examples/py/exchanges.md`
- **Size**: 1,155 bytes
- **Lines**: 65
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Exchanges](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys

import ccxt  # noqa: E402


def style(s, style):
    return style + s + '\033[0m'


def green(s):
    return style(s, '\033[92m')


def blue(s):
    return style(s, '\033[94m')


def yellow(s):
    return style(s, '\033[93m')


def red(s):
    return style(s, '\033[91m')


def pink(s):
    return style(s, '\033[95m')


def bold(s):
    return style(s, '\033[1m')


def underline(s):
    return style(s, '\033[4m')


def log(*args):
    print(' '.join([str(arg) for arg in args]))


exchanges = {}

for id in ccxt.exchanges:
    exchange = getattr(ccxt, id)
    exchanges[id] = exchange()

log('The ccxt library supports', green(str(len(ccxt.exchanges))), 'exchanges:')

# output a table of all exchanges
log(pink('{:<15} {:<15} {:<15}'.format('id', 'name', 'URL')))
tuples = list(ccxt.Exchange.keysort(exchanges).items())
for (id, params) in tuples:
    exchange = exchanges[id]
    website = exchange.urls['www'][0] if type(exchange.urls['www']) is list else exchange.urls['www']
    log('{:<15} {:<15} {:<15}'.format(exchange.id, exchange.name, website))
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/exchanges.md`.

**Functions defined**: green, red, style, bold, underline, yellow, pink, log, blue

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 65
- Code lines: 35
- Comment lines: 2
- Blank lines: 28

### Main Components

**Functions** (9):
- `blue()`
- `bold()`
- `green()`
- `log()`
- `pink()`
- `red()`
- `style()`
- `underline()`
- `yellow()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

