# Documentation: python/ccxt/abstract/btcturk.py

## File Metadata

- **Path**: `python/ccxt/abstract/btcturk.py`
- **Size**: 1,777 bytes
- **Lines**: 21
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_orderbook = publicGetOrderbook = Entry('orderbook', 'public', 'GET', {'cost': 1})
    public_get_ticker = publicGetTicker = Entry('ticker', 'public', 'GET', {'cost': 0.1})
    public_get_trades = publicGetTrades = Entry('trades', 'public', 'GET', {'cost': 1})
    public_get_ohlc = publicGetOhlc = Entry('ohlc', 'public', 'GET', {'cost': 1})
    public_get_server_exchangeinfo = publicGetServerExchangeinfo = Entry('server/exchangeinfo', 'public', 'GET', {'cost': 1})
    private_get_users_balances = privateGetUsersBalances = Entry('users/balances', 'private', 'GET', {'cost': 1})
    private_get_openorders = privateGetOpenOrders = Entry('openOrders', 'private', 'GET', {'cost': 1})
    private_get_allorders = privateGetAllOrders = Entry('allOrders', 'private', 'GET', {'cost': 1})
    private_get_users_transactions_trade = privateGetUsersTransactionsTrade = Entry('users/transactions/trade', 'private', 'GET', {'cost': 1})
    private_post_users_transactions_crypto = privatePostUsersTransactionsCrypto = Entry('users/transactions/crypto', 'private', 'POST', {'cost': 1})
    private_post_users_transactions_fiat = privatePostUsersTransactionsFiat = Entry('users/transactions/fiat', 'private', 'POST', {'cost': 1})
    private_post_order = privatePostOrder = Entry('order', 'private', 'POST', {'cost': 1})
    private_post_cancelorder = privatePostCancelOrder = Entry('cancelOrder', 'private', 'POST', {'cost': 1})
    private_delete_order = privateDeleteOrder = Entry('order', 'private', 'DELETE', {'cost': 1})
    graph_get_ohlcs = graphGetOhlcs = Entry('ohlcs', 'graph', 'GET', {'cost': 1})
    graph_get_klines_history = graphGetKlinesHistory = Entry('klines/history', 'graph', 'GET', {'cost': 1})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/btcturk.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 18
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `ImplicitAPI`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/abstract/btcturk.py
```

