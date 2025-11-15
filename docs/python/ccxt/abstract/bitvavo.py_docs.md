# Documentation: python/ccxt/abstract/bitvavo.py

## File Metadata

- **Path**: `python/ccxt/abstract/bitvavo.py`
- **Size**: 2,357 bytes
- **Lines**: 28
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_time = publicGetTime = Entry('time', 'public', 'GET', {'cost': 1})
    public_get_markets = publicGetMarkets = Entry('markets', 'public', 'GET', {'cost': 1})
    public_get_assets = publicGetAssets = Entry('assets', 'public', 'GET', {'cost': 1})
    public_get_market_book = publicGetMarketBook = Entry('{market}/book', 'public', 'GET', {'cost': 1})
    public_get_market_trades = publicGetMarketTrades = Entry('{market}/trades', 'public', 'GET', {'cost': 5})
    public_get_market_candles = publicGetMarketCandles = Entry('{market}/candles', 'public', 'GET', {'cost': 1})
    public_get_ticker_price = publicGetTickerPrice = Entry('ticker/price', 'public', 'GET', {'cost': 1})
    public_get_ticker_book = publicGetTickerBook = Entry('ticker/book', 'public', 'GET', {'cost': 1})
    public_get_ticker_24h = publicGetTicker24h = Entry('ticker/24h', 'public', 'GET', {'cost': 1, 'noMarket': 25})
    private_get_account = privateGetAccount = Entry('account', 'private', 'GET', {'cost': 1})
    private_get_order = privateGetOrder = Entry('order', 'private', 'GET', {'cost': 1})
    private_get_orders = privateGetOrders = Entry('orders', 'private', 'GET', {'cost': 5})
    private_get_ordersopen = privateGetOrdersOpen = Entry('ordersOpen', 'private', 'GET', {'cost': 1, 'noMarket': 25})
    private_get_trades = privateGetTrades = Entry('trades', 'private', 'GET', {'cost': 5})
    private_get_balance = privateGetBalance = Entry('balance', 'private', 'GET', {'cost': 5})
    private_get_deposit = privateGetDeposit = Entry('deposit', 'private', 'GET', {'cost': 1})
    private_get_deposithistory = privateGetDepositHistory = Entry('depositHistory', 'private', 'GET', {'cost': 5})
    private_get_withdrawalhistory = privateGetWithdrawalHistory = Entry('withdrawalHistory', 'private', 'GET', {'cost': 5})
    private_post_order = privatePostOrder = Entry('order', 'private', 'POST', {'cost': 1})
    private_post_withdrawal = privatePostWithdrawal = Entry('withdrawal', 'private', 'POST', {'cost': 1})
    private_put_order = privatePutOrder = Entry('order', 'private', 'PUT', {'cost': 1})
    private_delete_order = privateDeleteOrder = Entry('order', 'private', 'DELETE', {'cost': 1})
    private_delete_orders = privateDeleteOrders = Entry('orders', 'private', 'DELETE', {'cost': 1})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/bitvavo.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 25
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
python python/ccxt/abstract/bitvavo.py
```

