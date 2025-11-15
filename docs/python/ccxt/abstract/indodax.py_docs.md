# Documentation: python/ccxt/abstract/indodax.py

## File Metadata

- **Path**: `python/ccxt/abstract/indodax.py`
- **Size**: 2,488 bytes
- **Lines**: 27
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_api_server_time = publicGetApiServerTime = Entry('api/server_time', 'public', 'GET', {'cost': 5})
    public_get_api_pairs = publicGetApiPairs = Entry('api/pairs', 'public', 'GET', {'cost': 5})
    public_get_api_price_increments = publicGetApiPriceIncrements = Entry('api/price_increments', 'public', 'GET', {'cost': 5})
    public_get_api_summaries = publicGetApiSummaries = Entry('api/summaries', 'public', 'GET', {'cost': 5})
    public_get_api_ticker_pair = publicGetApiTickerPair = Entry('api/ticker/{pair}', 'public', 'GET', {'cost': 5})
    public_get_api_ticker_all = publicGetApiTickerAll = Entry('api/ticker_all', 'public', 'GET', {'cost': 5})
    public_get_api_trades_pair = publicGetApiTradesPair = Entry('api/trades/{pair}', 'public', 'GET', {'cost': 5})
    public_get_api_depth_pair = publicGetApiDepthPair = Entry('api/depth/{pair}', 'public', 'GET', {'cost': 5})
    public_get_tradingview_history_v2 = publicGetTradingviewHistoryV2 = Entry('tradingview/history_v2', 'public', 'GET', {'cost': 5})
    private_post_getinfo = privatePostGetInfo = Entry('getInfo', 'private', 'POST', {'cost': 4})
    private_post_transhistory = privatePostTransHistory = Entry('transHistory', 'private', 'POST', {'cost': 4})
    private_post_trade = privatePostTrade = Entry('trade', 'private', 'POST', {'cost': 1})
    private_post_tradehistory = privatePostTradeHistory = Entry('tradeHistory', 'private', 'POST', {'cost': 4})
    private_post_openorders = privatePostOpenOrders = Entry('openOrders', 'private', 'POST', {'cost': 4})
    private_post_orderhistory = privatePostOrderHistory = Entry('orderHistory', 'private', 'POST', {'cost': 4})
    private_post_getorder = privatePostGetOrder = Entry('getOrder', 'private', 'POST', {'cost': 4})
    private_post_cancelorder = privatePostCancelOrder = Entry('cancelOrder', 'private', 'POST', {'cost': 4})
    private_post_withdrawfee = privatePostWithdrawFee = Entry('withdrawFee', 'private', 'POST', {'cost': 4})
    private_post_withdrawcoin = privatePostWithdrawCoin = Entry('withdrawCoin', 'private', 'POST', {'cost': 4})
    private_post_listdownline = privatePostListDownline = Entry('listDownline', 'private', 'POST', {'cost': 4})
    private_post_checkdownline = privatePostCheckDownline = Entry('checkDownline', 'private', 'POST', {'cost': 4})
    private_post_createvoucher = privatePostCreateVoucher = Entry('createVoucher', 'private', 'POST', {'cost': 4})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/indodax.py`.

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
python python/ccxt/abstract/indodax.py
```

