# Documentation: python/ccxt/abstract/oceanex.py

## File Metadata

- **Path**: `python/ccxt/abstract/oceanex.py`
- **Size**: 2,307 bytes
- **Lines**: 28
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_markets = publicGetMarkets = Entry('markets', 'public', 'GET', {})
    public_get_tickers_pair = publicGetTickersPair = Entry('tickers/{pair}', 'public', 'GET', {})
    public_get_tickers_multi = publicGetTickersMulti = Entry('tickers_multi', 'public', 'GET', {})
    public_get_order_book = publicGetOrderBook = Entry('order_book', 'public', 'GET', {})
    public_get_order_book_multi = publicGetOrderBookMulti = Entry('order_book/multi', 'public', 'GET', {})
    public_get_fees_trading = publicGetFeesTrading = Entry('fees/trading', 'public', 'GET', {})
    public_get_trades = publicGetTrades = Entry('trades', 'public', 'GET', {})
    public_get_timestamp = publicGetTimestamp = Entry('timestamp', 'public', 'GET', {})
    public_post_k = publicPostK = Entry('k', 'public', 'POST', {})
    private_get_key = privateGetKey = Entry('key', 'private', 'GET', {})
    private_get_members_me = privateGetMembersMe = Entry('members/me', 'private', 'GET', {})
    private_get_orders = privateGetOrders = Entry('orders', 'private', 'GET', {})
    private_get_orders_filter = privateGetOrdersFilter = Entry('orders/filter', 'private', 'GET', {})
    private_post_orders = privatePostOrders = Entry('orders', 'private', 'POST', {})
    private_post_orders_multi = privatePostOrdersMulti = Entry('orders/multi', 'private', 'POST', {})
    private_post_order_delete = privatePostOrderDelete = Entry('order/delete', 'private', 'POST', {})
    private_post_order_delete_multi = privatePostOrderDeleteMulti = Entry('order/delete/multi', 'private', 'POST', {})
    private_post_orders_clear = privatePostOrdersClear = Entry('orders/clear', 'private', 'POST', {})
    private_post_withdraws_special_new = privatePostWithdrawsSpecialNew = Entry('/withdraws/special/new', 'private', 'POST', {})
    private_post_deposit_address = privatePostDepositAddress = Entry('/deposit_address', 'private', 'POST', {})
    private_post_deposit_addresses = privatePostDepositAddresses = Entry('/deposit_addresses', 'private', 'POST', {})
    private_post_deposit_history = privatePostDepositHistory = Entry('/deposit_history', 'private', 'POST', {})
    private_post_withdraw_history = privatePostWithdrawHistory = Entry('/withdraw_history', 'private', 'POST', {})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/oceanex.py`.

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
python python/ccxt/abstract/oceanex.py
```

