# Documentation: wiki/examples/py/withdraw-from-one-exchange-to-another.md

## File Metadata

- **Path**: `wiki/examples/py/withdraw-from-one-exchange-to-another.md`
- **Size**: 1,036 bytes
- **Lines**: 48
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Withdraw From One Exchange To Another](./examples/py/)


 ```python
 import ccxt
import sys
from pprint import pprint

print('python', sys.version)
print('CCXT Version:', ccxt.__version__)

binance = ccxt.binance({
    "apiKey": 'YOUR_BINANCE_API_KEY',
    "secret": 'YOUR_BINANCE_SECRET',
    'options': {
        'fetchCurrencies': True,
    },
})
binance.verbose = True

kucoin = ccxt.kucoin({
    'apiKey': 'YOUR_KUCOIN_API_KEY',
    'secret': 'YOUR_KUCOIN_SECRET',
    'password': 'YOUR_KUCOIN_API_PASSWORD',
})
kucoin.verbose = True

binance.load_markets()
kucoin.load_markets()

code = 'USDT'
amount = 40

params = {'network': 'TRC20'}

deposit = binance.fetchDepositAddress(code, params)

print('-----------------------------------------------------------')
print(deposit)
print('-----------------------------------------------------------')

withdrawal = kucoin.withdraw(code, amount, deposit['address'], deposit['tag'], params)

print('-----------------------------------------------------------')

pprint(withdrawal)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/withdraw-from-one-exchange-to-another.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 34
- Comment lines: 0
- Blank lines: 14

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

