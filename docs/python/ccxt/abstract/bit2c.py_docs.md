# Documentation: python/ccxt/abstract/bit2c.py

## File Metadata

- **Path**: `python/ccxt/abstract/bit2c.py`
- **Size**: 2,830 bytes
- **Lines**: 28
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_exchanges_pair_ticker = publicGetExchangesPairTicker = Entry('Exchanges/{pair}/Ticker', 'public', 'GET', {})
    public_get_exchanges_pair_orderbook = publicGetExchangesPairOrderbook = Entry('Exchanges/{pair}/orderbook', 'public', 'GET', {})
    public_get_exchanges_pair_trades = publicGetExchangesPairTrades = Entry('Exchanges/{pair}/trades', 'public', 'GET', {})
    public_get_exchanges_pair_lasttrades = publicGetExchangesPairLasttrades = Entry('Exchanges/{pair}/lasttrades', 'public', 'GET', {})
    private_post_merchant_createcheckout = privatePostMerchantCreateCheckout = Entry('Merchant/CreateCheckout', 'private', 'POST', {})
    private_post_funds_addcoinfundsrequest = privatePostFundsAddCoinFundsRequest = Entry('Funds/AddCoinFundsRequest', 'private', 'POST', {})
    private_post_order_addfund = privatePostOrderAddFund = Entry('Order/AddFund', 'private', 'POST', {})
    private_post_order_addorder = privatePostOrderAddOrder = Entry('Order/AddOrder', 'private', 'POST', {})
    private_post_order_getbyid = privatePostOrderGetById = Entry('Order/GetById', 'private', 'POST', {})
    private_post_order_addordermarketpricebuy = privatePostOrderAddOrderMarketPriceBuy = Entry('Order/AddOrderMarketPriceBuy', 'private', 'POST', {})
    private_post_order_addordermarketpricesell = privatePostOrderAddOrderMarketPriceSell = Entry('Order/AddOrderMarketPriceSell', 'private', 'POST', {})
    private_post_order_cancelorder = privatePostOrderCancelOrder = Entry('Order/CancelOrder', 'private', 'POST', {})
    private_post_order_addcoinfundsrequest = privatePostOrderAddCoinFundsRequest = Entry('Order/AddCoinFundsRequest', 'private', 'POST', {})
    private_post_order_addstoporder = privatePostOrderAddStopOrder = Entry('Order/AddStopOrder', 'private', 'POST', {})
    private_post_payment_getmyid = privatePostPaymentGetMyId = Entry('Payment/GetMyId', 'private', 'POST', {})
    private_post_payment_send = privatePostPaymentSend = Entry('Payment/Send', 'private', 'POST', {})
    private_post_payment_pay = privatePostPaymentPay = Entry('Payment/Pay', 'private', 'POST', {})
    private_get_account_balance = privateGetAccountBalance = Entry('Account/Balance', 'private', 'GET', {})
    private_get_account_balance_v2 = privateGetAccountBalanceV2 = Entry('Account/Balance/v2', 'private', 'GET', {})
    private_get_order_myorders = privateGetOrderMyOrders = Entry('Order/MyOrders', 'private', 'GET', {})
    private_get_order_getbyid = privateGetOrderGetById = Entry('Order/GetById', 'private', 'GET', {})
    private_get_order_accounthistory = privateGetOrderAccountHistory = Entry('Order/AccountHistory', 'private', 'GET', {})
    private_get_order_orderhistory = privateGetOrderOrderHistory = Entry('Order/OrderHistory', 'private', 'GET', {})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/bit2c.py`.

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
python python/ccxt/abstract/bit2c.py
```

