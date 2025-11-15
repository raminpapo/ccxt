# Documentation: python/ccxt/abstract/onetrading.py

## File Metadata

- **Path**: `python/ccxt/abstract/onetrading.py`
- **Size**: 2,278 bytes
- **Lines**: 24
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_currencies = publicGetCurrencies = Entry('currencies', 'public', 'GET', {})
    public_get_candlesticks_instrument_code = publicGetCandlesticksInstrumentCode = Entry('candlesticks/{instrument_code}', 'public', 'GET', {})
    public_get_fees = publicGetFees = Entry('fees', 'public', 'GET', {})
    public_get_instruments = publicGetInstruments = Entry('instruments', 'public', 'GET', {})
    public_get_order_book_instrument_code = publicGetOrderBookInstrumentCode = Entry('order-book/{instrument_code}', 'public', 'GET', {})
    public_get_market_ticker = publicGetMarketTicker = Entry('market-ticker', 'public', 'GET', {})
    public_get_market_ticker_instrument_code = publicGetMarketTickerInstrumentCode = Entry('market-ticker/{instrument_code}', 'public', 'GET', {})
    public_get_time = publicGetTime = Entry('time', 'public', 'GET', {})
    private_get_account_balances = privateGetAccountBalances = Entry('account/balances', 'private', 'GET', {})
    private_get_account_fees = privateGetAccountFees = Entry('account/fees', 'private', 'GET', {})
    private_get_account_orders = privateGetAccountOrders = Entry('account/orders', 'private', 'GET', {})
    private_get_account_orders_order_id = privateGetAccountOrdersOrderId = Entry('account/orders/{order_id}', 'private', 'GET', {})
    private_get_account_orders_order_id_trades = privateGetAccountOrdersOrderIdTrades = Entry('account/orders/{order_id}/trades', 'private', 'GET', {})
    private_get_account_trades = privateGetAccountTrades = Entry('account/trades', 'private', 'GET', {})
    private_get_account_trades_trade_id = privateGetAccountTradesTradeId = Entry('account/trades/{trade_id}', 'private', 'GET', {})
    private_post_account_orders = privatePostAccountOrders = Entry('account/orders', 'private', 'POST', {})
    private_delete_account_orders = privateDeleteAccountOrders = Entry('account/orders', 'private', 'DELETE', {})
    private_delete_account_orders_order_id = privateDeleteAccountOrdersOrderId = Entry('account/orders/{order_id}', 'private', 'DELETE', {})
    private_delete_account_orders_client_client_id = privateDeleteAccountOrdersClientClientId = Entry('account/orders/client/{client_id}', 'private', 'DELETE', {})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/onetrading.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 21
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
python python/ccxt/abstract/onetrading.py
```

