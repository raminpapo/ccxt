# Documentation: python/ccxt/abstract/p2b.py

## File Metadata

- **Path**: `python/ccxt/abstract/p2b.py`
- **Size**: 2,054 bytes
- **Lines**: 23
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_markets = publicGetMarkets = Entry('markets', 'public', 'GET', {'cost': 1})
    public_get_market = publicGetMarket = Entry('market', 'public', 'GET', {'cost': 1})
    public_get_tickers = publicGetTickers = Entry('tickers', 'public', 'GET', {'cost': 1})
    public_get_ticker = publicGetTicker = Entry('ticker', 'public', 'GET', {'cost': 1})
    public_get_book = publicGetBook = Entry('book', 'public', 'GET', {'cost': 1})
    public_get_history = publicGetHistory = Entry('history', 'public', 'GET', {'cost': 1})
    public_get_depth_result = publicGetDepthResult = Entry('depth/result', 'public', 'GET', {'cost': 1})
    public_get_market_kline = publicGetMarketKline = Entry('market/kline', 'public', 'GET', {'cost': 1})
    private_post_account_balances = privatePostAccountBalances = Entry('account/balances', 'private', 'POST', {'cost': 1})
    private_post_account_balance = privatePostAccountBalance = Entry('account/balance', 'private', 'POST', {'cost': 1})
    private_post_order_new = privatePostOrderNew = Entry('order/new', 'private', 'POST', {'cost': 1})
    private_post_order_cancel = privatePostOrderCancel = Entry('order/cancel', 'private', 'POST', {'cost': 1})
    private_post_orders = privatePostOrders = Entry('orders', 'private', 'POST', {'cost': 1})
    private_post_account_market_order_history = privatePostAccountMarketOrderHistory = Entry('account/market_order_history', 'private', 'POST', {'cost': 1})
    private_post_account_market_deal_history = privatePostAccountMarketDealHistory = Entry('account/market_deal_history', 'private', 'POST', {'cost': 1})
    private_post_account_order = privatePostAccountOrder = Entry('account/order', 'private', 'POST', {'cost': 1})
    private_post_account_order_history = privatePostAccountOrderHistory = Entry('account/order_history', 'private', 'POST', {'cost': 1})
    private_post_account_executed_history = privatePostAccountExecutedHistory = Entry('account/executed_history', 'private', 'POST', {'cost': 1})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/p2b.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 20
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
python python/ccxt/abstract/p2b.py
```

