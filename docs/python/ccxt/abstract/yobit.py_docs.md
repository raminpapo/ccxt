# Documentation: python/ccxt/abstract/yobit.py

## File Metadata

- **Path**: `python/ccxt/abstract/yobit.py`
- **Size**: 1,339 bytes
- **Lines**: 17
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_depth_pair = publicGetDepthPair = Entry('depth/{pair}', 'public', 'GET', {'cost': 1})
    public_get_info = publicGetInfo = Entry('info', 'public', 'GET', {'cost': 1})
    public_get_ticker_pair = publicGetTickerPair = Entry('ticker/{pair}', 'public', 'GET', {'cost': 1})
    public_get_trades_pair = publicGetTradesPair = Entry('trades/{pair}', 'public', 'GET', {'cost': 1})
    private_post_activeorders = privatePostActiveOrders = Entry('ActiveOrders', 'private', 'POST', {'cost': 1})
    private_post_cancelorder = privatePostCancelOrder = Entry('CancelOrder', 'private', 'POST', {'cost': 1})
    private_post_getdepositaddress = privatePostGetDepositAddress = Entry('GetDepositAddress', 'private', 'POST', {'cost': 1})
    private_post_getinfo = privatePostGetInfo = Entry('getInfo', 'private', 'POST', {'cost': 1})
    private_post_orderinfo = privatePostOrderInfo = Entry('OrderInfo', 'private', 'POST', {'cost': 1})
    private_post_trade = privatePostTrade = Entry('Trade', 'private', 'POST', {'cost': 1})
    private_post_tradehistory = privatePostTradeHistory = Entry('TradeHistory', 'private', 'POST', {'cost': 1})
    private_post_withdrawcoinstoaddress = privatePostWithdrawCoinsToAddress = Entry('WithdrawCoinsToAddress', 'private', 'POST', {'cost': 1})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/yobit.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 14
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
python python/ccxt/abstract/yobit.py
```

