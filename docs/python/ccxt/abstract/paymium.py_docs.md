# Documentation: python/ccxt/abstract/paymium.py

## File Metadata

- **Path**: `python/ccxt/abstract/paymium.py`
- **Size**: 2,843 bytes
- **Lines**: 29
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_countries = publicGetCountries = Entry('countries', 'public', 'GET', {})
    public_get_currencies = publicGetCurrencies = Entry('currencies', 'public', 'GET', {})
    public_get_data_currency_ticker = publicGetDataCurrencyTicker = Entry('data/{currency}/ticker', 'public', 'GET', {})
    public_get_data_currency_trades = publicGetDataCurrencyTrades = Entry('data/{currency}/trades', 'public', 'GET', {})
    public_get_data_currency_depth = publicGetDataCurrencyDepth = Entry('data/{currency}/depth', 'public', 'GET', {})
    public_get_bitcoin_charts_id_trades = publicGetBitcoinChartsIdTrades = Entry('bitcoin_charts/{id}/trades', 'public', 'GET', {})
    public_get_bitcoin_charts_id_depth = publicGetBitcoinChartsIdDepth = Entry('bitcoin_charts/{id}/depth', 'public', 'GET', {})
    private_get_user = privateGetUser = Entry('user', 'private', 'GET', {})
    private_get_user_addresses = privateGetUserAddresses = Entry('user/addresses', 'private', 'GET', {})
    private_get_user_addresses_address = privateGetUserAddressesAddress = Entry('user/addresses/{address}', 'private', 'GET', {})
    private_get_user_orders = privateGetUserOrders = Entry('user/orders', 'private', 'GET', {})
    private_get_user_orders_uuid = privateGetUserOrdersUuid = Entry('user/orders/{uuid}', 'private', 'GET', {})
    private_get_user_price_alerts = privateGetUserPriceAlerts = Entry('user/price_alerts', 'private', 'GET', {})
    private_get_merchant_get_payment_uuid = privateGetMerchantGetPaymentUuid = Entry('merchant/get_payment/{uuid}', 'private', 'GET', {})
    private_post_user_addresses = privatePostUserAddresses = Entry('user/addresses', 'private', 'POST', {})
    private_post_user_orders = privatePostUserOrders = Entry('user/orders', 'private', 'POST', {})
    private_post_user_withdrawals = privatePostUserWithdrawals = Entry('user/withdrawals', 'private', 'POST', {})
    private_post_user_email_transfers = privatePostUserEmailTransfers = Entry('user/email_transfers', 'private', 'POST', {})
    private_post_user_payment_requests = privatePostUserPaymentRequests = Entry('user/payment_requests', 'private', 'POST', {})
    private_post_user_price_alerts = privatePostUserPriceAlerts = Entry('user/price_alerts', 'private', 'POST', {})
    private_post_merchant_create_payment = privatePostMerchantCreatePayment = Entry('merchant/create_payment', 'private', 'POST', {})
    private_delete_user_orders_uuid = privateDeleteUserOrdersUuid = Entry('user/orders/{uuid}', 'private', 'DELETE', {})
    private_delete_user_orders_uuid_cancel = privateDeleteUserOrdersUuidCancel = Entry('user/orders/{uuid}/cancel', 'private', 'DELETE', {})
    private_delete_user_price_alerts_id = privateDeleteUserPriceAlertsId = Entry('user/price_alerts/{id}', 'private', 'DELETE', {})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/paymium.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 26
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
python python/ccxt/abstract/paymium.py
```

