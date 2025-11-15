# Documentation: js/src/pro/ascendex.d.ts

## File Metadata

- **Path**: `js/src/pro/ascendex.d.ts`
- **Size**: 6,167 bytes
- **Lines**: 100
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import ascendexRest from '../ascendex.js';
import type { Int, Str, OrderBook, Order, Trade, OHLCV, Balances, Bool } from '../base/types.js';
import Client from '../base/ws/Client.js';
export default class ascendex extends ascendexRest {
    describe(): any;
    watchPublic(messageHash: any, params?: {}): Promise<any>;
    watchPublicMultiple(messageHashes: any, params?: {}): Promise<any>;
    watchPrivate(channel: any, messageHash: any, params?: {}): Promise<any>;
    /**
     * @method
     * @name ascendex#watchOHLCV
     * @description watches historical candlestick data containing the open, high, low, and close price, and the volume of a market
     * @see https://ascendex.github.io/ascendex-pro-api/#channel-bar-data
     * @param {string} symbol unified symbol of the market to fetch OHLCV data for
     * @param {string} timeframe the length of time each candle represents
     * @param {int} [since] timestamp in ms of the earliest candle to fetch
     * @param {int} [limit] the maximum amount of candles to fetch
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @returns {int[][]} A list of candles ordered as timestamp, open, high, low, close, volume
     */
    watchOHLCV(symbol: string, timeframe?: string, since?: Int, limit?: Int, params?: {}): Promise<OHLCV[]>;
    handleOHLCV(client: Client, message: any): any;
    /**
     * @method
     * @name ascendex#watchTrades
     * @description get the list of most recent trades for a particular symbol
     * @see https://ascendex.github.io/ascendex-pro-api/#channel-market-trades
     * @param {string} symbol unified symbol of the market to fetch trades for
     * @param {int} [since] timestamp in ms of the earliest trade to fetch
     * @param {int} [limit] the maximum amount of trades to fetch
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @returns {object[]} a list of [trade structures]{@link https://docs.ccxt.com/#/?id=public-trades}
     */
    watchTrades(symbol: string, since?: Int, limit?: Int, params?: {}): Promise<Trade[]>;
    /**
     * @method
     * @name ascendex#watchTradesForSymbols
     * @description get the list of most recent trades for a list of symbols
     * @see https://ascendex.github.io/ascendex-pro-api/#channel-market-trades
     * @param {string[]} symbols unified symbol of the market to fetch trades for
     * @param {int} [since] timestamp in ms of the earliest trade to fetch
     * @param {int} [limit] the maximum amount of trades to fetch
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @param {string} [params.name] the name of the method to call, 'trade' or 'aggTrade', default is 'trade'
     * @returns {object[]} a list of [trade structures]{@link https://docs.ccxt.com/#/?id=public-trades}
     */
    watchTradesForSymbols(symbols: string[], since?: Int, limit?: Int, params?: {}): Promise<Trade[]>;
    handleTrades(client: Client, message: any): void;
    /**
     * @method
     * @name ascendex#watchOrderBook
     * @description watches information on open orders with bid (buy) and ask (sell) prices, volumes and other data
     * @see https://ascendex.github.io/ascendex-pro-api/#channel-level-2-order-book-updates
     * @param {string} symbol unified symbol of the market to fetch the order book for
     * @param {int} [limit] the maximum amount of order book entries to return
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @returns {object} A dictionary of [order book structures]{@link https://docs.ccxt.com/#/?id=order-book-structure} indexed by market symbols
     */
    watchOrderBook(symbol: string, limit?: Int, params?: {}): Promise<OrderBook>;
    watchOrderBookSnapshot(symbol: string, limit?: Int, params?: {}): Promise<any>;
    fetchOrderBookSnapshotCustom(symbol: string, limit?: Int, params?: {}): Promise<import("../base/ws/OrderBook.js").OrderBook>;
    handleOrderBookSnapshot(client: Client, message: any): void;
    handleOrderBook(client: Client, message: any): void;
    handleDelta(bookside: any, delta: any): void;
    handleDeltas(bookside: any, deltas: any): void;
    handleOrderBookMessage(client: Client, message: any, orderbook: any): any;
    /**
     * @method
     * @name ascendex#watchBalance
     * @description watch balance and get the amount of funds available for trading or funds locked in orders
     * @see https://ascendex.github.io/ascendex-pro-api/#channel-order-and-balance
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @returns {object} a [balance structure]{@link https://docs.ccxt.com/#/?id=balance-structure}
     */
    watchBalance(params?: {}): Promise<Balances>;
    handleBalance(client: Client, message: any): void;
    /**
     * @method
     * @name ascendex#watchOrders
     * @see https://ascendex.github.io/ascendex-pro-api/#channel-order-and-balance
     * @description watches information on multiple orders made by the user
     * @param {string} symbol unified market symbol of the market orders were made in
     * @param {int} [since] the earliest time in ms to fetch orders for
     * @param {int} [limit] the maximum number of order structures to retrieve
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @returns {object[]} a list of [order structures]{@link https://docs.ccxt.com/#/?id=order-structure}
     */
    watchOrders(symbol?: Str, since?: Int, limit?: Int, params?: {}): Promise<Order[]>;
    handleOrder(client: Client, message: any): void;
    parseWsOrder(order: any, market?: any): Order;
    handleErrorMessage(client: Client, message: any): Bool;
    handleAuthenticate(client: Client, message: any): void;
    handleMessage(client: Client, message: any): void;
    handleSubscriptionStatus(client: Client, message: any): any;
    handleOrderBookSubscription(client: Client, message: any): void;
    pong(client: any, message: any): Promise<void>;
    handlePing(client: Client, message: any): void;
    authenticate(url: any, params?: {}): Promise<any>;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/pro/ascendex.d.ts`.

**Classes defined**: ascendex

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 100
- Code lines: 99
- Comment lines: 64
- Blank lines: -63

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../base/ws/Client.js` (imported)
- `../ascendex.js` (imported)
- `../base/types.js` (imported)
- `../base/ws/Client.js` (referenced)
- `../ascendex.js` (referenced)
- `../base/types.js` (referenced)
- `../base/ws/OrderBook.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/pro/ascendex.d.ts
```

