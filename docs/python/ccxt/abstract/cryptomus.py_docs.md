# Documentation: python/ccxt/abstract/cryptomus.py

## File Metadata

- **Path**: `python/ccxt/abstract/cryptomus.py`
- **Size**: 2,672 bytes
- **Lines**: 21
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_v2_user_api_exchange_markets = publicGetV2UserApiExchangeMarkets = Entry('v2/user-api/exchange/markets', 'public', 'GET', {'cost': 1})
    public_get_v2_user_api_exchange_market_price = publicGetV2UserApiExchangeMarketPrice = Entry('v2/user-api/exchange/market/price', 'public', 'GET', {'cost': 1})
    public_get_v1_exchange_market_assets = publicGetV1ExchangeMarketAssets = Entry('v1/exchange/market/assets', 'public', 'GET', {'cost': 1})
    public_get_v1_exchange_market_order_book_currencypair = publicGetV1ExchangeMarketOrderBookCurrencyPair = Entry('v1/exchange/market/order-book/{currencyPair}', 'public', 'GET', {'cost': 1})
    public_get_v1_exchange_market_tickers = publicGetV1ExchangeMarketTickers = Entry('v1/exchange/market/tickers', 'public', 'GET', {'cost': 1})
    public_get_v1_exchange_market_trades_currencypair = publicGetV1ExchangeMarketTradesCurrencyPair = Entry('v1/exchange/market/trades/{currencyPair}', 'public', 'GET', {'cost': 1})
    private_get_v2_user_api_exchange_orders = privateGetV2UserApiExchangeOrders = Entry('v2/user-api/exchange/orders', 'private', 'GET', {'cost': 1})
    private_get_v2_user_api_exchange_orders_history = privateGetV2UserApiExchangeOrdersHistory = Entry('v2/user-api/exchange/orders/history', 'private', 'GET', {'cost': 1})
    private_get_v2_user_api_exchange_account_balance = privateGetV2UserApiExchangeAccountBalance = Entry('v2/user-api/exchange/account/balance', 'private', 'GET', {'cost': 1})
    private_get_v2_user_api_exchange_account_tariffs = privateGetV2UserApiExchangeAccountTariffs = Entry('v2/user-api/exchange/account/tariffs', 'private', 'GET', {'cost': 1})
    private_get_v2_user_api_payment_services = privateGetV2UserApiPaymentServices = Entry('v2/user-api/payment/services', 'private', 'GET', {'cost': 1})
    private_get_v2_user_api_payout_services = privateGetV2UserApiPayoutServices = Entry('v2/user-api/payout/services', 'private', 'GET', {'cost': 1})
    private_get_v2_user_api_transaction_list = privateGetV2UserApiTransactionList = Entry('v2/user-api/transaction/list', 'private', 'GET', {'cost': 1})
    private_post_v2_user_api_exchange_orders = privatePostV2UserApiExchangeOrders = Entry('v2/user-api/exchange/orders', 'private', 'POST', {'cost': 1})
    private_post_v2_user_api_exchange_orders_market = privatePostV2UserApiExchangeOrdersMarket = Entry('v2/user-api/exchange/orders/market', 'private', 'POST', {'cost': 1})
    private_delete_v2_user_api_exchange_orders_orderid = privateDeleteV2UserApiExchangeOrdersOrderId = Entry('v2/user-api/exchange/orders/{orderId}', 'private', 'DELETE', {'cost': 1})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/cryptomus.py`.

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
python python/ccxt/abstract/cryptomus.py
```

