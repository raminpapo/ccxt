# Documentation: python/ccxt/abstract/bitopro.py

## File Metadata

- **Path**: `python/ccxt/abstract/bitopro.py`
- **Size**: 3,400 bytes
- **Lines**: 31
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_order_book_pair = publicGetOrderBookPair = Entry('order-book/{pair}', 'public', 'GET', {'cost': 1})
    public_get_tickers = publicGetTickers = Entry('tickers', 'public', 'GET', {'cost': 1})
    public_get_tickers_pair = publicGetTickersPair = Entry('tickers/{pair}', 'public', 'GET', {'cost': 1})
    public_get_trades_pair = publicGetTradesPair = Entry('trades/{pair}', 'public', 'GET', {'cost': 1})
    public_get_provisioning_currencies = publicGetProvisioningCurrencies = Entry('provisioning/currencies', 'public', 'GET', {'cost': 1})
    public_get_provisioning_trading_pairs = publicGetProvisioningTradingPairs = Entry('provisioning/trading-pairs', 'public', 'GET', {'cost': 1})
    public_get_provisioning_limitations_and_fees = publicGetProvisioningLimitationsAndFees = Entry('provisioning/limitations-and-fees', 'public', 'GET', {'cost': 1})
    public_get_trading_history_pair = publicGetTradingHistoryPair = Entry('trading-history/{pair}', 'public', 'GET', {'cost': 1})
    public_get_price_otc_currency = publicGetPriceOtcCurrency = Entry('price/otc/{currency}', 'public', 'GET', {'cost': 1})
    private_get_accounts_balance = privateGetAccountsBalance = Entry('accounts/balance', 'private', 'GET', {'cost': 1})
    private_get_orders_history = privateGetOrdersHistory = Entry('orders/history', 'private', 'GET', {'cost': 1})
    private_get_orders_all_pair = privateGetOrdersAllPair = Entry('orders/all/{pair}', 'private', 'GET', {'cost': 1})
    private_get_orders_trades_pair = privateGetOrdersTradesPair = Entry('orders/trades/{pair}', 'private', 'GET', {'cost': 1})
    private_get_orders_pair_orderid = privateGetOrdersPairOrderId = Entry('orders/{pair}/{orderId}', 'private', 'GET', {'cost': 1})
    private_get_wallet_withdraw_currency_serial = privateGetWalletWithdrawCurrencySerial = Entry('wallet/withdraw/{currency}/{serial}', 'private', 'GET', {'cost': 1})
    private_get_wallet_withdraw_currency_id_id = privateGetWalletWithdrawCurrencyIdId = Entry('wallet/withdraw/{currency}/id/{id}', 'private', 'GET', {'cost': 1})
    private_get_wallet_deposithistory_currency = privateGetWalletDepositHistoryCurrency = Entry('wallet/depositHistory/{currency}', 'private', 'GET', {'cost': 1})
    private_get_wallet_withdrawhistory_currency = privateGetWalletWithdrawHistoryCurrency = Entry('wallet/withdrawHistory/{currency}', 'private', 'GET', {'cost': 1})
    private_get_orders_open = privateGetOrdersOpen = Entry('orders/open', 'private', 'GET', {'cost': 1})
    private_post_orders_pair = privatePostOrdersPair = Entry('orders/{pair}', 'private', 'POST', {'cost': 0.5})
    private_post_orders_batch = privatePostOrdersBatch = Entry('orders/batch', 'private', 'POST', {'cost': 6.666666666666667})
    private_post_wallet_withdraw_currency = privatePostWalletWithdrawCurrency = Entry('wallet/withdraw/{currency}', 'private', 'POST', {'cost': 10})
    private_put_orders = privatePutOrders = Entry('orders', 'private', 'PUT', {'cost': 5})
    private_delete_orders_pair_id = privateDeleteOrdersPairId = Entry('orders/{pair}/{id}', 'private', 'DELETE', {'cost': 0.6666666666666666})
    private_delete_orders_all = privateDeleteOrdersAll = Entry('orders/all', 'private', 'DELETE', {'cost': 5})
    private_delete_orders_pair = privateDeleteOrdersPair = Entry('orders/{pair}', 'private', 'DELETE', {'cost': 5})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/bitopro.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 28
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
python python/ccxt/abstract/bitopro.py
```

