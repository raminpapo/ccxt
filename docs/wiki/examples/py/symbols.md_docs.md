# Documentation: wiki/examples/py/symbols.md

## File Metadata

- **Path**: `wiki/examples/py/symbols.md`
- **Size**: 1,947 bytes
- **Lines**: 97
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Symbols](./examples/py/)


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


def dump(*args):
    print(' '.join([str(arg) for arg in args]))


def print_supported_exchanges():
    dump('Supported exchanges:', green(', '.join(ccxt.exchanges)))


try:

    id = sys.argv[1]  # get exchange id from command line arguments

    # check if the exchange is supported by ccxt
    exchange_found = id in ccxt.exchanges

    if exchange_found:
        dump('Instantiating', green(id), 'exchange')

        # instantiate the exchange by id
        exchange = getattr(ccxt, id)({
            # 'proxy':'https://cors-anywhere.herokuapp.com/',
        })

        # load all markets from the exchange
        markets = exchange.load_markets()

        # output a list of all market symbols
        dump(green(id), 'has', len(exchange.symbols), 'symbols:', exchange.symbols)

        tuples = list(ccxt.Exchange.keysort(markets).items())

        # debug
        for (k, v) in tuples:
            print(v)

        # output a table of all markets
        dump(pink('{:<15} {:<15} {:<15} {:<15}'.format('id', 'symbol', 'base', 'quote')))

        for (k, v) in tuples:
            dump('{:<15} {:<15} {:<15} {:<15}'.format(v['id'], v['symbol'], v['base'], v['quote']))

    else:

        dump('Exchange ' + red(id) + ' not found')
        print_supported_exchanges()

except Exception as e:
    dump('[' + type(e).__name__ + ']', str(e))
    dump("Usage: python " + sys.argv[0], green('id'))
    print_supported_exchanges()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/symbols.md`.

**Functions defined**: green, print_supported_exchanges, red, style, bold, underline, yellow, pink, dump, blue

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 97
- Code lines: 48
- Comment lines: 8
- Blank lines: 41

### Main Components

**Functions** (10):
- `blue()`
- `bold()`
- `dump()`
- `green()`
- `pink()`
- `print_supported_exchanges()`
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

