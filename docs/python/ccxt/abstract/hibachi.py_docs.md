# Documentation: python/ccxt/abstract/hibachi.py

## File Metadata

- **Path**: `python/ccxt/abstract/hibachi.py`
- **Size**: 2,769 bytes
- **Lines**: 27
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_market_exchange_info = publicGetMarketExchangeInfo = Entry('market/exchange-info', 'public', 'GET', {'cost': 1})
    public_get_market_data_trades = publicGetMarketDataTrades = Entry('market/data/trades', 'public', 'GET', {'cost': 1})
    public_get_market_data_prices = publicGetMarketDataPrices = Entry('market/data/prices', 'public', 'GET', {'cost': 1})
    public_get_market_data_stats = publicGetMarketDataStats = Entry('market/data/stats', 'public', 'GET', {'cost': 1})
    public_get_market_data_klines = publicGetMarketDataKlines = Entry('market/data/klines', 'public', 'GET', {'cost': 1})
    public_get_market_data_orderbook = publicGetMarketDataOrderbook = Entry('market/data/orderbook', 'public', 'GET', {'cost': 1})
    public_get_market_data_open_interest = publicGetMarketDataOpenInterest = Entry('market/data/open-interest', 'public', 'GET', {'cost': 1})
    public_get_market_data_funding_rates = publicGetMarketDataFundingRates = Entry('market/data/funding-rates', 'public', 'GET', {'cost': 1})
    public_get_exchange_utc_timestamp = publicGetExchangeUtcTimestamp = Entry('exchange/utc-timestamp', 'public', 'GET', {'cost': 1})
    private_get_capital_deposit_info = privateGetCapitalDepositInfo = Entry('capital/deposit-info', 'private', 'GET', {'cost': 1})
    private_get_capital_history = privateGetCapitalHistory = Entry('capital/history', 'private', 'GET', {'cost': 1})
    private_get_trade_account_trading_history = privateGetTradeAccountTradingHistory = Entry('trade/account/trading_history', 'private', 'GET', {'cost': 1})
    private_get_trade_account_info = privateGetTradeAccountInfo = Entry('trade/account/info', 'private', 'GET', {'cost': 1})
    private_get_trade_order = privateGetTradeOrder = Entry('trade/order', 'private', 'GET', {'cost': 1})
    private_get_trade_account_trades = privateGetTradeAccountTrades = Entry('trade/account/trades', 'private', 'GET', {'cost': 1})
    private_get_trade_orders = privateGetTradeOrders = Entry('trade/orders', 'private', 'GET', {'cost': 1})
    private_put_trade_order = privatePutTradeOrder = Entry('trade/order', 'private', 'PUT', {'cost': 1})
    private_delete_trade_order = privateDeleteTradeOrder = Entry('trade/order', 'private', 'DELETE', {'cost': 1})
    private_delete_trade_orders = privateDeleteTradeOrders = Entry('trade/orders', 'private', 'DELETE', {'cost': 1})
    private_post_trade_order = privatePostTradeOrder = Entry('trade/order', 'private', 'POST', {'cost': 1})
    private_post_trade_orders = privatePostTradeOrders = Entry('trade/orders', 'private', 'POST', {'cost': 1})
    private_post_capital_withdraw = privatePostCapitalWithdraw = Entry('capital/withdraw', 'private', 'POST', {'cost': 1})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/hibachi.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 24
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
python python/ccxt/abstract/hibachi.py
```

