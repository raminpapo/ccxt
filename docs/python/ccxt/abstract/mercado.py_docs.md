# Documentation: python/ccxt/abstract/mercado.py

## File Metadata

- **Path**: `python/ccxt/abstract/mercado.py`
- **Size**: 2,357 bytes
- **Lines**: 26
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ccxt.base.types import Entry


class ImplicitAPI:
    public_get_coins = publicGetCoins = Entry('coins', 'public', 'GET', {})
    public_get_coin_orderbook = publicGetCoinOrderbook = Entry('{coin}/orderbook/', 'public', 'GET', {})
    public_get_coin_ticker = publicGetCoinTicker = Entry('{coin}/ticker/', 'public', 'GET', {})
    public_get_coin_trades = publicGetCoinTrades = Entry('{coin}/trades/', 'public', 'GET', {})
    public_get_coin_trades_from = publicGetCoinTradesFrom = Entry('{coin}/trades/{from}/', 'public', 'GET', {})
    public_get_coin_trades_from_to = publicGetCoinTradesFromTo = Entry('{coin}/trades/{from}/{to}', 'public', 'GET', {})
    public_get_coin_day_summary_year_month_day = publicGetCoinDaySummaryYearMonthDay = Entry('{coin}/day-summary/{year}/{month}/{day}/', 'public', 'GET', {})
    private_post_cancel_order = privatePostCancelOrder = Entry('cancel_order', 'private', 'POST', {})
    private_post_get_account_info = privatePostGetAccountInfo = Entry('get_account_info', 'private', 'POST', {})
    private_post_get_order = privatePostGetOrder = Entry('get_order', 'private', 'POST', {})
    private_post_get_withdrawal = privatePostGetWithdrawal = Entry('get_withdrawal', 'private', 'POST', {})
    private_post_list_system_messages = privatePostListSystemMessages = Entry('list_system_messages', 'private', 'POST', {})
    private_post_list_orders = privatePostListOrders = Entry('list_orders', 'private', 'POST', {})
    private_post_list_orderbook = privatePostListOrderbook = Entry('list_orderbook', 'private', 'POST', {})
    private_post_place_buy_order = privatePostPlaceBuyOrder = Entry('place_buy_order', 'private', 'POST', {})
    private_post_place_sell_order = privatePostPlaceSellOrder = Entry('place_sell_order', 'private', 'POST', {})
    private_post_place_market_buy_order = privatePostPlaceMarketBuyOrder = Entry('place_market_buy_order', 'private', 'POST', {})
    private_post_place_market_sell_order = privatePostPlaceMarketSellOrder = Entry('place_market_sell_order', 'private', 'POST', {})
    private_post_withdraw_coin = privatePostWithdrawCoin = Entry('withdraw_coin', 'private', 'POST', {})
    v4public_get_coin_candle = v4PublicGetCoinCandle = Entry('{coin}/candle/', 'v4Public', 'GET', {})
    v4publicnet_get_candles = v4PublicNetGetCandles = Entry('candles', 'v4PublicNet', 'GET', {})

```

## High-Level Overview

This is a Python file located at `python/ccxt/abstract/mercado.py`.

**Classes defined**: ImplicitAPI

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 23
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
python python/ccxt/abstract/mercado.py
```

