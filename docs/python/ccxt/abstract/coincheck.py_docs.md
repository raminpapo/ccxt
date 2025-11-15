# Documentation: python/ccxt/abstract/coincheck.py

## File Metadata

- **Path**: `python/ccxt/abstract/coincheck.py`
- **Size**: 3,417 bytes
- **Lines**: 34
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_exchange_orders_rate = publicGetExchangeOrdersRate = Entry('exchange/orders/rate', 'public', 'GET', {})
    public_get_order_books = publicGetOrderBooks = Entry('order_books', 'public', 'GET', {})
    public_get_rate_pair = publicGetRatePair = Entry('rate/{pair}', 'public', 'GET', {})
    public_get_ticker = publicGetTicker = Entry('ticker', 'public', 'GET', {})
    public_get_trades = publicGetTrades = Entry('trades', 'public', 'GET', {})
    private_get_accounts = privateGetAccounts = Entry('accounts', 'private', 'GET', {})
    private_get_accounts_balance = privateGetAccountsBalance = Entry('accounts/balance', 'private', 'GET', {})
    private_get_accounts_leverage_balance = privateGetAccountsLeverageBalance = Entry('accounts/leverage_balance', 'private', 'GET', {})
    private_get_bank_accounts = privateGetBankAccounts = Entry('bank_accounts', 'private', 'GET', {})
    private_get_deposit_money = privateGetDepositMoney = Entry('deposit_money', 'private', 'GET', {})
    private_get_exchange_orders_opens = privateGetExchangeOrdersOpens = Entry('exchange/orders/opens', 'private', 'GET', {})
    private_get_exchange_orders_transactions = privateGetExchangeOrdersTransactions = Entry('exchange/orders/transactions', 'private', 'GET', {})
    private_get_exchange_orders_transactions_pagination = privateGetExchangeOrdersTransactionsPagination = Entry('exchange/orders/transactions_pagination', 'private', 'GET', {})
    private_get_exchange_leverage_positions = privateGetExchangeLeveragePositions = Entry('exchange/leverage/positions', 'private', 'GET', {})
    private_get_lending_borrows_matches = privateGetLendingBorrowsMatches = Entry('lending/borrows/matches', 'private', 'GET', {})
    private_get_send_money = privateGetSendMoney = Entry('send_money', 'private', 'GET', {})
    private_get_withdraws = privateGetWithdraws = Entry('withdraws', 'private', 'GET', {})
    private_post_bank_accounts = privatePostBankAccounts = Entry('bank_accounts', 'private', 'POST', {})
    private_post_deposit_money_id_fast = privatePostDepositMoneyIdFast = Entry('deposit_money/{id}/fast', 'private', 'POST', {})
    private_post_exchange_orders = privatePostExchangeOrders = Entry('exchange/orders', 'private', 'POST', {})
    private_post_exchange_transfers_to_leverage = privatePostExchangeTransfersToLeverage = Entry('exchange/transfers/to_leverage', 'private', 'POST', {})
    private_post_exchange_transfers_from_leverage = privatePostExchangeTransfersFromLeverage = Entry('exchange/transfers/from_leverage', 'private', 'POST', {})
    private_post_lending_borrows = privatePostLendingBorrows = Entry('lending/borrows', 'private', 'POST', {})
    private_post_lending_borrows_id_repay = privatePostLendingBorrowsIdRepay = Entry('lending/borrows/{id}/repay', 'private', 'POST', {})
    private_post_send_money = privatePostSendMoney = Entry('send_money', 'private', 'POST', {})
    private_post_withdraws = privatePostWithdraws = Entry('withdraws', 'private', 'POST', {})
    private_delete_bank_accounts_id = privateDeleteBankAccountsId = Entry('bank_accounts/{id}', 'private', 'DELETE', {})
    private_delete_exchange_orders_id = privateDeleteExchangeOrdersId = Entry('exchange/orders/{id}', 'private', 'DELETE', {})
    private_delete_withdraws_id = privateDeleteWithdrawsId = Entry('withdraws/{id}', 'private', 'DELETE', {})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/coincheck.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 31
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
python python/ccxt/abstract/coincheck.py
```

