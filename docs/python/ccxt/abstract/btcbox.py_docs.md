# Documentation: python/ccxt/abstract/btcbox.py

## File Metadata

- **Path**: `python/ccxt/abstract/btcbox.py`
- **Size**: 1,044 bytes
- **Lines**: 16
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_depth = publicGetDepth = Entry('depth', 'public', 'GET', {})
    public_get_orders = publicGetOrders = Entry('orders', 'public', 'GET', {})
    public_get_ticker = publicGetTicker = Entry('ticker', 'public', 'GET', {})
    public_get_tickers = publicGetTickers = Entry('tickers', 'public', 'GET', {})
    private_post_balance = privatePostBalance = Entry('balance', 'private', 'POST', {})
    private_post_trade_add = privatePostTradeAdd = Entry('trade_add', 'private', 'POST', {})
    private_post_trade_cancel = privatePostTradeCancel = Entry('trade_cancel', 'private', 'POST', {})
    private_post_trade_list = privatePostTradeList = Entry('trade_list', 'private', 'POST', {})
    private_post_trade_view = privatePostTradeView = Entry('trade_view', 'private', 'POST', {})
    private_post_wallet = privatePostWallet = Entry('wallet', 'private', 'POST', {})
    webapi_get_ajax_coin_coininfo = webApiGetAjaxCoinCoinInfo = Entry('ajax/coin/coinInfo', 'webApi', 'GET', {})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/btcbox.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 16
- Code lines: 13
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
python python/ccxt/abstract/btcbox.py
```

