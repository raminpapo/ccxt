# Documentation: python/ccxt/abstract/hollaex.py

## File Metadata

- **Path**: `python/ccxt/abstract/hollaex.py`
- **Size**: 2,906 bytes
- **Lines**: 34
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_health = publicGetHealth = Entry('health', 'public', 'GET', {'cost': 1})
    public_get_constants = publicGetConstants = Entry('constants', 'public', 'GET', {'cost': 1})
    public_get_kit = publicGetKit = Entry('kit', 'public', 'GET', {'cost': 1})
    public_get_tiers = publicGetTiers = Entry('tiers', 'public', 'GET', {'cost': 1})
    public_get_ticker = publicGetTicker = Entry('ticker', 'public', 'GET', {'cost': 1})
    public_get_tickers = publicGetTickers = Entry('tickers', 'public', 'GET', {'cost': 1})
    public_get_orderbook = publicGetOrderbook = Entry('orderbook', 'public', 'GET', {'cost': 1})
    public_get_orderbooks = publicGetOrderbooks = Entry('orderbooks', 'public', 'GET', {'cost': 1})
    public_get_trades = publicGetTrades = Entry('trades', 'public', 'GET', {'cost': 1})
    public_get_chart = publicGetChart = Entry('chart', 'public', 'GET', {'cost': 1})
    public_get_charts = publicGetCharts = Entry('charts', 'public', 'GET', {'cost': 1})
    public_get_minicharts = publicGetMinicharts = Entry('minicharts', 'public', 'GET', {'cost': 1})
    public_get_oracle_prices = publicGetOraclePrices = Entry('oracle/prices', 'public', 'GET', {'cost': 1})
    public_get_quick_trade = publicGetQuickTrade = Entry('quick-trade', 'public', 'GET', {'cost': 1})
    public_get_udf_config = publicGetUdfConfig = Entry('udf/config', 'public', 'GET', {'cost': 1})
    public_get_udf_history = publicGetUdfHistory = Entry('udf/history', 'public', 'GET', {'cost': 1})
    public_get_udf_symbols = publicGetUdfSymbols = Entry('udf/symbols', 'public', 'GET', {'cost': 1})
    private_get_user = privateGetUser = Entry('user', 'private', 'GET', {'cost': 1})
    private_get_user_balance = privateGetUserBalance = Entry('user/balance', 'private', 'GET', {'cost': 1})
    private_get_user_deposits = privateGetUserDeposits = Entry('user/deposits', 'private', 'GET', {'cost': 1})
    private_get_user_withdrawals = privateGetUserWithdrawals = Entry('user/withdrawals', 'private', 'GET', {'cost': 1})
    private_get_user_withdrawal_fee = privateGetUserWithdrawalFee = Entry('user/withdrawal/fee', 'private', 'GET', {'cost': 1})
    private_get_user_trades = privateGetUserTrades = Entry('user/trades', 'private', 'GET', {'cost': 1})
    private_get_orders = privateGetOrders = Entry('orders', 'private', 'GET', {'cost': 1})
    private_get_order = privateGetOrder = Entry('order', 'private', 'GET', {'cost': 1})
    private_post_user_withdrawal = privatePostUserWithdrawal = Entry('user/withdrawal', 'private', 'POST', {'cost': 1})
    private_post_order = privatePostOrder = Entry('order', 'private', 'POST', {'cost': 1})
    private_delete_order_all = privateDeleteOrderAll = Entry('order/all', 'private', 'DELETE', {'cost': 1})
    private_delete_order = privateDeleteOrder = Entry('order', 'private', 'DELETE', {'cost': 1})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/hollaex.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 31
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
python python/ccxt/abstract/hollaex.py
```

