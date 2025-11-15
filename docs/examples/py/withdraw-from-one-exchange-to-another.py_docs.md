# Documentation: examples/py/withdraw-from-one-exchange-to-another.py

## File Metadata

- **Path**: `examples/py/withdraw-from-one-exchange-to-another.py`
- **Size**: 959 bytes
- **Lines**: 43
- **Type**: Python
- **Extension**: .py


## Original Source Code

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

## High-Level Overview

This is a Python file located at `examples/py/withdraw-from-one-exchange-to-another.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 31
- Comment lines: 0
- Blank lines: 12

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/withdraw-from-one-exchange-to-another.py
```

