# Documentation: python/ccxt/abstract/blockchaincom.py

## File Metadata

- **Path**: `python/ccxt/abstract/blockchaincom.py`
- **Size**: 2,638 bytes
- **Lines**: 29
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_tickers = publicGetTickers = Entry('tickers', 'public', 'GET', {'cost': 1})
    public_get_tickers_symbol = publicGetTickersSymbol = Entry('tickers/{symbol}', 'public', 'GET', {'cost': 1})
    public_get_symbols = publicGetSymbols = Entry('symbols', 'public', 'GET', {'cost': 1})
    public_get_symbols_symbol = publicGetSymbolsSymbol = Entry('symbols/{symbol}', 'public', 'GET', {'cost': 1})
    public_get_l2_symbol = publicGetL2Symbol = Entry('l2/{symbol}', 'public', 'GET', {'cost': 1})
    public_get_l3_symbol = publicGetL3Symbol = Entry('l3/{symbol}', 'public', 'GET', {'cost': 1})
    private_get_fees = privateGetFees = Entry('fees', 'private', 'GET', {'cost': 1})
    private_get_orders = privateGetOrders = Entry('orders', 'private', 'GET', {'cost': 1})
    private_get_orders_orderid = privateGetOrdersOrderId = Entry('orders/{orderId}', 'private', 'GET', {'cost': 1})
    private_get_trades = privateGetTrades = Entry('trades', 'private', 'GET', {'cost': 1})
    private_get_fills = privateGetFills = Entry('fills', 'private', 'GET', {'cost': 1})
    private_get_deposits = privateGetDeposits = Entry('deposits', 'private', 'GET', {'cost': 1})
    private_get_deposits_depositid = privateGetDepositsDepositId = Entry('deposits/{depositId}', 'private', 'GET', {'cost': 1})
    private_get_accounts = privateGetAccounts = Entry('accounts', 'private', 'GET', {'cost': 1})
    private_get_accounts_account_currency = privateGetAccountsAccountCurrency = Entry('accounts/{account}/{currency}', 'private', 'GET', {'cost': 1})
    private_get_whitelist = privateGetWhitelist = Entry('whitelist', 'private', 'GET', {'cost': 1})
    private_get_whitelist_currency = privateGetWhitelistCurrency = Entry('whitelist/{currency}', 'private', 'GET', {'cost': 1})
    private_get_withdrawals = privateGetWithdrawals = Entry('withdrawals', 'private', 'GET', {'cost': 1})
    private_get_withdrawals_withdrawalid = privateGetWithdrawalsWithdrawalId = Entry('withdrawals/{withdrawalId}', 'private', 'GET', {'cost': 1})
    private_post_orders = privatePostOrders = Entry('orders', 'private', 'POST', {'cost': 1})
    private_post_deposits_currency = privatePostDepositsCurrency = Entry('deposits/{currency}', 'private', 'POST', {'cost': 1})
    private_post_withdrawals = privatePostWithdrawals = Entry('withdrawals', 'private', 'POST', {'cost': 1})
    private_delete_orders = privateDeleteOrders = Entry('orders', 'private', 'DELETE', {'cost': 1})
    private_delete_orders_orderid = privateDeleteOrdersOrderId = Entry('orders/{orderId}', 'private', 'DELETE', {'cost': 1})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/blockchaincom.py`.

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
python python/ccxt/abstract/blockchaincom.py
```

