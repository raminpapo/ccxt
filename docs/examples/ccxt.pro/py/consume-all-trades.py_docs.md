# Documentation: examples/ccxt.pro/py/consume-all-trades.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/consume-all-trades.py`
- **Size**: 793 bytes
- **Lines**: 23
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt.pro
from asyncio import run


async def consume_all_trades(exchange, symbol):
    await exchange.load_markets()
    while True:
        try:
            trades = await exchange.watch_trades(symbol)
            print('----------------------------------------------------------------------')
            print(exchange.iso8601(exchange.milliseconds()), 'received', len(trades), 'new', symbol, 'trades:')
            for trade in trades:
                print(exchange.id, symbol, trade['id'], trade['datetime'], trade['amount'], trade['price'])
            exchange.trades[symbol].clear()
        except Exception as e:
            print(type(e).__name__, str(e))
    await exchange.close()


exchange = ccxt.pro.bitmex()
symbol = 'BTC/USD'
run(consume_all_trades(exchange, symbol))

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/consume-all-trades.py`.

**Functions defined**: consume_all_trades

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 18
- Comment lines: 0
- Blank lines: 5

### Main Components

**Functions** (1):
- `consume_all_trades()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/ccxt.pro/py/consume-all-trades.py
```

