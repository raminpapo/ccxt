# Documentation: python/ccxt/abstract/zaif.py

## File Metadata

- **Path**: `python/ccxt/abstract/zaif.py`
- **Size**: 3,935 bytes
- **Lines**: 39
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_depth_pair = publicGetDepthPair = Entry('depth/{pair}', 'public', 'GET', {'cost': 1})
    public_get_currencies_pair = publicGetCurrenciesPair = Entry('currencies/{pair}', 'public', 'GET', {'cost': 1})
    public_get_currencies_all = publicGetCurrenciesAll = Entry('currencies/all', 'public', 'GET', {'cost': 1})
    public_get_currency_pairs_pair = publicGetCurrencyPairsPair = Entry('currency_pairs/{pair}', 'public', 'GET', {'cost': 1})
    public_get_currency_pairs_all = publicGetCurrencyPairsAll = Entry('currency_pairs/all', 'public', 'GET', {'cost': 1})
    public_get_last_price_pair = publicGetLastPricePair = Entry('last_price/{pair}', 'public', 'GET', {'cost': 1})
    public_get_ticker_pair = publicGetTickerPair = Entry('ticker/{pair}', 'public', 'GET', {'cost': 1})
    public_get_trades_pair = publicGetTradesPair = Entry('trades/{pair}', 'public', 'GET', {'cost': 1})
    private_post_active_orders = privatePostActiveOrders = Entry('active_orders', 'private', 'POST', {'cost': 5})
    private_post_cancel_order = privatePostCancelOrder = Entry('cancel_order', 'private', 'POST', {'cost': 5})
    private_post_deposit_history = privatePostDepositHistory = Entry('deposit_history', 'private', 'POST', {'cost': 5})
    private_post_get_id_info = privatePostGetIdInfo = Entry('get_id_info', 'private', 'POST', {'cost': 5})
    private_post_get_info = privatePostGetInfo = Entry('get_info', 'private', 'POST', {'cost': 10})
    private_post_get_info2 = privatePostGetInfo2 = Entry('get_info2', 'private', 'POST', {'cost': 5})
    private_post_get_personal_info = privatePostGetPersonalInfo = Entry('get_personal_info', 'private', 'POST', {'cost': 5})
    private_post_trade = privatePostTrade = Entry('trade', 'private', 'POST', {'cost': 5})
    private_post_trade_history = privatePostTradeHistory = Entry('trade_history', 'private', 'POST', {'cost': 50})
    private_post_withdraw = privatePostWithdraw = Entry('withdraw', 'private', 'POST', {'cost': 5})
    private_post_withdraw_history = privatePostWithdrawHistory = Entry('withdraw_history', 'private', 'POST', {'cost': 5})
    ecapi_post_createinvoice = ecapiPostCreateInvoice = Entry('createInvoice', 'ecapi', 'POST', {'cost': 1})
    ecapi_post_getinvoice = ecapiPostGetInvoice = Entry('getInvoice', 'ecapi', 'POST', {'cost': 1})
    ecapi_post_getinvoiceidsbyordernumber = ecapiPostGetInvoiceIdsByOrderNumber = Entry('getInvoiceIdsByOrderNumber', 'ecapi', 'POST', {'cost': 1})
    ecapi_post_cancelinvoice = ecapiPostCancelInvoice = Entry('cancelInvoice', 'ecapi', 'POST', {'cost': 1})
    tlapi_post_get_positions = tlapiPostGetPositions = Entry('get_positions', 'tlapi', 'POST', {'cost': 66})
    tlapi_post_position_history = tlapiPostPositionHistory = Entry('position_history', 'tlapi', 'POST', {'cost': 66})
    tlapi_post_active_positions = tlapiPostActivePositions = Entry('active_positions', 'tlapi', 'POST', {'cost': 5})
    tlapi_post_create_position = tlapiPostCreatePosition = Entry('create_position', 'tlapi', 'POST', {'cost': 33})
    tlapi_post_change_position = tlapiPostChangePosition = Entry('change_position', 'tlapi', 'POST', {'cost': 33})
    tlapi_post_cancel_position = tlapiPostCancelPosition = Entry('cancel_position', 'tlapi', 'POST', {'cost': 33})
    fapi_get_groups_group_id = fapiGetGroupsGroupId = Entry('groups/{group_id}', 'fapi', 'GET', {'cost': 1})
    fapi_get_last_price_group_id_pair = fapiGetLastPriceGroupIdPair = Entry('last_price/{group_id}/{pair}', 'fapi', 'GET', {'cost': 1})
    fapi_get_ticker_group_id_pair = fapiGetTickerGroupIdPair = Entry('ticker/{group_id}/{pair}', 'fapi', 'GET', {'cost': 1})
    fapi_get_trades_group_id_pair = fapiGetTradesGroupIdPair = Entry('trades/{group_id}/{pair}', 'fapi', 'GET', {'cost': 1})
    fapi_get_depth_group_id_pair = fapiGetDepthGroupIdPair = Entry('depth/{group_id}/{pair}', 'fapi', 'GET', {'cost': 1})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/zaif.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 36
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
python python/ccxt/abstract/zaif.py
```

