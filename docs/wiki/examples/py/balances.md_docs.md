# Documentation: wiki/examples/py/balances.md

## File Metadata

- **Path**: `wiki/examples/py/balances.md`
- **Size**: 1,875 bytes
- **Lines**: 87
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Balances](./examples/py/)


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


# instantiate exchanges

coinbasepro = ccxt.coinbasepro({
    'apiKey': '92560ffae9b8a01d012726c698bcb2f1',  # standard
    'secret': '9aHjPmW+EtRRKN/OiZGjXh8OxyThnDL4mMDre4Ghvn8wjMniAr5jdEZJLN/knW6FHeQyiz3dPIL5ytnF0Y6Xwg==',
    'password': '6kszf4aci8r',  # requires a password!
})

coinbasepro.urls['api'] = coinbasepro.urls['test']  # use the testnet

hitbtc = ccxt.hitbtc({
    'apiKey': '18339694544745d9357f9e7c0f7c41bb',
    'secret': '8340a60fb4e9fc73a169c26c7a7926f5',
})

try:
    # fetch account balance from the exchange
    coinbaseproBalance = coinbasepro.fetch_balance()

    # output the result
    dump(green(coinbasepro.name), 'balance', coinbaseproBalance)

    # fetch another one
    hitbtcBalance = hitbtc.fetch_balance()

    # output the result
    dump(green(hitbtc.name), 'balance', hitbtcBalance)

except ccxt.DDoSProtection as e:
    print(type(e).__name__, e.args, 'DDoS Protection (ignoring)')
except ccxt.RequestTimeout as e:
    print(type(e).__name__, e.args, 'Request Timeout (ignoring)')
except ccxt.ExchangeNotAvailable as e:
    print(type(e).__name__, e.args, 'Exchange Not Available due to downtime or maintenance (ignoring)')
except ccxt.AuthenticationError as e:
    print(type(e).__name__, e.args, 'Authentication Error (missing API keys, ignoring)')
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/balances.md`.

**Functions defined**: green, red, style, bold, underline, yellow, pink, dump, blue

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 87
- Code lines: 47
- Comment lines: 6
- Blank lines: 34

### Main Components

**Functions** (9):
- `blue()`
- `bold()`
- `dump()`
- `green()`
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

