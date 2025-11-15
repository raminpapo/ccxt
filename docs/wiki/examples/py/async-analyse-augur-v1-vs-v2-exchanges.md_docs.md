# Documentation: wiki/examples/py/async-analyse-augur-v1-vs-v2-exchanges.md

## File Metadata

- **Path**: `wiki/examples/py/async-analyse-augur-v1-vs-v2-exchanges.md`
- **Size**: 2,729 bytes
- **Lines**: 92
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Analyse Augur V1 Vs V2 Exchanges](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys
from typing import Optional


import ccxt.async_support as ccxt


unchecked_exchanges = []


def is_symbol_match(
    symbol: str,
    allowed_infix: str,
    disallowed_infix: Optional[str] = None
) -> bool:
    """This function is to keep everything that has allowed_infix=REP, but
    excpude everything that has disallowed_infix=DREP, except for when you encounter something like: REPV2/DREP

    Returns True if this symbol is allowed to be in the list.

    Args:
        symbol (str): the symbol to evaluate
        allowed_infix (str): the allowed infix for both currencies in this symbol
        disallowed_infix (Optional[str], optional): the disallowed infix for when the other currency is does not have the allowed infix. Defaults to None.

    Returns:
        bool:
    """
    parts = symbol.split('/')

    if disallowed_infix:
        for i, currency in enumerate(parts):
            if disallowed_infix in currency:
                # if one currency contains for instance disallowed_infix=DREP,
                # then the other currency must contain allowed_infix=REP to be allowed, else disallow
                return allowed_infix in parts[i + 1 % 2]

    return any([allowed_infix in currency for currency in parts])


async def check_symbol_infix(exchange, symbol_infix, exclude_infix=None):
    try:
        await exchange.load_markets()
    except Exception as exc:
        # exchange could not load_markets for some reason...
        unchecked_exchanges.append(exchange.id)
    else:
        matching_symbols = [
            symbol for symbol in exchange.symbols
            if is_symbol_match(symbol, symbol_infix, exclude_infix)
        ]
        if matching_symbols:
            print(
                f'on exchange {exchange.id} these symbols contain {symbol_infix}:'
            )
            for symbol in matching_symbols:
                print(f' - {symbol}:')
                # print(f'   exchange specific market info: {exchange.markets[symbol]["info"]}')
                if 'V1' in symbol:
                    print('   - marked V1')
                if 'V2' in symbol:
                    print('   - marked V2')
            print()

    await exchange.close()


async def main():
    tasks = []
    for exchange_id in ccxt.exchanges:
        exchange = getattr(ccxt, exchange_id)()
        tasks.append(
            check_symbol_infix(
                exchange, symbol_infix='REP', exclude_infix='DREP'
            )
        )
    await asyncio.gather(*tasks)

    print(f'errors for exchanges: {", ".join(unchecked_exchanges)}')


asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-analyse-augur-v1-vs-v2-exchanges.md`.

**Functions defined**: is_symbol_match, main, is, check_symbol_infix

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 92
- Code lines: 64
- Comment lines: 7
- Blank lines: 21

### Main Components

**Functions** (4):
- `check_symbol_infix()`
- `is()`
- `is_symbol_match()`
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

