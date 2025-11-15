# Documentation: python/ccxt/abstract/bithumb.py

## File Metadata

- **Path**: `python/ccxt/abstract/bithumb.py`
- **Size**: 3,443 bytes
- **Lines**: 33
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_ticker_all_quoteid = publicGetTickerALLQuoteId = Entry('ticker/ALL_{quoteId}', 'public', 'GET', {})
    public_get_ticker_baseid_quoteid = publicGetTickerBaseIdQuoteId = Entry('ticker/{baseId}_{quoteId}', 'public', 'GET', {})
    public_get_orderbook_all_quoteid = publicGetOrderbookALLQuoteId = Entry('orderbook/ALL_{quoteId}', 'public', 'GET', {})
    public_get_orderbook_baseid_quoteid = publicGetOrderbookBaseIdQuoteId = Entry('orderbook/{baseId}_{quoteId}', 'public', 'GET', {})
    public_get_transaction_history_baseid_quoteid = publicGetTransactionHistoryBaseIdQuoteId = Entry('transaction_history/{baseId}_{quoteId}', 'public', 'GET', {})
    public_get_network_info = publicGetNetworkInfo = Entry('network-info', 'public', 'GET', {})
    public_get_assetsstatus_multichain_all = publicGetAssetsstatusMultichainALL = Entry('assetsstatus/multichain/ALL', 'public', 'GET', {})
    public_get_assetsstatus_multichain_currency = publicGetAssetsstatusMultichainCurrency = Entry('assetsstatus/multichain/{currency}', 'public', 'GET', {})
    public_get_withdraw_minimum_all = publicGetWithdrawMinimumALL = Entry('withdraw/minimum/ALL', 'public', 'GET', {})
    public_get_withdraw_minimum_currency = publicGetWithdrawMinimumCurrency = Entry('withdraw/minimum/{currency}', 'public', 'GET', {})
    public_get_assetsstatus_all = publicGetAssetsstatusALL = Entry('assetsstatus/ALL', 'public', 'GET', {})
    public_get_assetsstatus_baseid = publicGetAssetsstatusBaseId = Entry('assetsstatus/{baseId}', 'public', 'GET', {})
    public_get_candlestick_baseid_quoteid_interval = publicGetCandlestickBaseIdQuoteIdInterval = Entry('candlestick/{baseId}_{quoteId}/{interval}', 'public', 'GET', {})
    private_post_info_account = privatePostInfoAccount = Entry('info/account', 'private', 'POST', {})
    private_post_info_balance = privatePostInfoBalance = Entry('info/balance', 'private', 'POST', {})
    private_post_info_wallet_address = privatePostInfoWalletAddress = Entry('info/wallet_address', 'private', 'POST', {})
    private_post_info_ticker = privatePostInfoTicker = Entry('info/ticker', 'private', 'POST', {})
    private_post_info_orders = privatePostInfoOrders = Entry('info/orders', 'private', 'POST', {})
    private_post_info_user_transactions = privatePostInfoUserTransactions = Entry('info/user_transactions', 'private', 'POST', {})
    private_post_info_order_detail = privatePostInfoOrderDetail = Entry('info/order_detail', 'private', 'POST', {})
    private_post_trade_place = privatePostTradePlace = Entry('trade/place', 'private', 'POST', {})
    private_post_trade_cancel = privatePostTradeCancel = Entry('trade/cancel', 'private', 'POST', {})
    private_post_trade_btc_withdrawal = privatePostTradeBtcWithdrawal = Entry('trade/btc_withdrawal', 'private', 'POST', {})
    private_post_trade_krw_deposit = privatePostTradeKrwDeposit = Entry('trade/krw_deposit', 'private', 'POST', {})
    private_post_trade_krw_withdrawal = privatePostTradeKrwWithdrawal = Entry('trade/krw_withdrawal', 'private', 'POST', {})
    private_post_trade_market_buy = privatePostTradeMarketBuy = Entry('trade/market_buy', 'private', 'POST', {})
    private_post_trade_market_sell = privatePostTradeMarketSell = Entry('trade/market_sell', 'private', 'POST', {})
    private_post_trade_stop_limit = privatePostTradeStopLimit = Entry('trade/stop_limit', 'private', 'POST', {})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/bithumb.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 30
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
python python/ccxt/abstract/bithumb.py
```

