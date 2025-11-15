# Documentation: python/ccxt/abstract/btcalpha.py

## File Metadata

- **Path**: `python/ccxt/abstract/btcalpha.py`
- **Size**: 1,380 bytes
- **Lines**: 19
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_currencies = publicGetCurrencies = Entry('currencies/', 'public', 'GET', {})
    public_get_pairs = publicGetPairs = Entry('pairs/', 'public', 'GET', {})
    public_get_orderbook_pair_name = publicGetOrderbookPairName = Entry('orderbook/{pair_name}', 'public', 'GET', {})
    public_get_exchanges = publicGetExchanges = Entry('exchanges/', 'public', 'GET', {})
    public_get_charts_pair_type_chart = publicGetChartsPairTypeChart = Entry('charts/{pair}/{type}/chart/', 'public', 'GET', {})
    public_get_ticker = publicGetTicker = Entry('ticker/', 'public', 'GET', {})
    private_get_wallets = privateGetWallets = Entry('wallets/', 'private', 'GET', {})
    private_get_orders_own = privateGetOrdersOwn = Entry('orders/own/', 'private', 'GET', {})
    private_get_order_id = privateGetOrderId = Entry('order/{id}/', 'private', 'GET', {})
    private_get_exchanges_own = privateGetExchangesOwn = Entry('exchanges/own/', 'private', 'GET', {})
    private_get_deposits = privateGetDeposits = Entry('deposits/', 'private', 'GET', {})
    private_get_withdraws = privateGetWithdraws = Entry('withdraws/', 'private', 'GET', {})
    private_post_order = privatePostOrder = Entry('order/', 'private', 'POST', {})
    private_post_order_cancel = privatePostOrderCancel = Entry('order-cancel/', 'private', 'POST', {})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/btcalpha.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 16
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
python python/ccxt/abstract/btcalpha.py
```

