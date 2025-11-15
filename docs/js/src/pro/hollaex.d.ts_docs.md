# Documentation: js/src/pro/hollaex.d.ts

## File Metadata

- **Path**: `js/src/pro/hollaex.d.ts`
- **Size**: 4,388 bytes
- **Lines**: 78
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import hollaexRest from '../hollaex.js';
import type { Int, Str, OrderBook, Order, Trade, Balances, Bool } from '../base/types.js';
import Client from '../base/ws/Client.js';
export default class hollaex extends hollaexRest {
    describe(): any;
    /**
     * @method
     * @name hollaex#watchOrderBook
     * @description watches information on open orders with bid (buy) and ask (sell) prices, volumes and other data
     * @see https://apidocs.hollaex.com/#sending-receiving-messages
     * @param {string} symbol unified symbol of the market to fetch the order book for
     * @param {int} [limit] the maximum amount of order book entries to return
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @returns {object} A dictionary of [order book structures]{@link https://docs.ccxt.com/#/?id=order-book-structure} indexed by market symbols
     */
    watchOrderBook(symbol: string, limit?: Int, params?: {}): Promise<OrderBook>;
    handleOrderBook(client: Client, message: any): void;
    /**
     * @method
     * @name hollaex#watchTrades
     * @description get the list of most recent trades for a particular symbol
     * @see https://apidocs.hollaex.com/#sending-receiving-messages
     * @param {string} symbol unified symbol of the market to fetch trades for
     * @param {int} [since] timestamp in ms of the earliest trade to fetch
     * @param {int} [limit] the maximum amount of trades to fetch
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @returns {object[]} a list of [trade structures]{@link https://docs.ccxt.com/#/?id=public-trades}
     */
    watchTrades(symbol: string, since?: Int, limit?: Int, params?: {}): Promise<Trade[]>;
    handleTrades(client: Client, message: any): void;
    /**
     * @method
     * @name hollaex#watchMyTrades
     * @description watches information on multiple trades made by the user
     * @see https://apidocs.hollaex.com/#sending-receiving-messages
     * @param {string} symbol unified market symbol of the market trades were made in
     * @param {int} [since] the earliest time in ms to fetch trades for
     * @param {int} [limit] the maximum number of trade structures to retrieve
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @returns {object[]} a list of [trade structures]{@link https://docs.ccxt.com/#/?id=trade-structure}
     */
    watchMyTrades(symbol?: Str, since?: Int, limit?: Int, params?: {}): Promise<Trade[]>;
    handleMyTrades(client: Client, message: any, subscription?: any): void;
    /**
     * @method
     * @name hollaex#watchOrders
     * @description watches information on multiple orders made by the user
     * @see https://apidocs.hollaex.com/#sending-receiving-messages
     * @param {string} symbol unified market symbol of the market orders were made in
     * @param {int} [since] the earliest time in ms to fetch orders for
     * @param {int} [limit] the maximum number of order structures to retrieve
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @returns {object[]} a list of [order structures]{@link https://docs.ccxt.com/#/?id=order-structure}
     */
    watchOrders(symbol?: Str, since?: Int, limit?: Int, params?: {}): Promise<Order[]>;
    handleOrder(client: Client, message: any, subscription?: any): void;
    /**
     * @method
     * @name hollaex#watchBalance
     * @description watch balance and get the amount of funds available for trading or funds locked in orders
     * @see https://apidocs.hollaex.com/#sending-receiving-messages
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @returns {object} a [balance structure]{@link https://docs.ccxt.com/#/?id=balance-structure}
     */
    watchBalance(params?: {}): Promise<Balances>;
    handleBalance(client: Client, message: any): void;
    watchPublic(messageHash: any, params?: {}): Promise<any>;
    watchPrivate(messageHash: any, params?: {}): Promise<any>;
    handleErrorMessage(client: Client, message: any): Bool;
    handleMessage(client: Client, message: any): void;
    ping(client: Client): {
        op: string;
    };
    handlePong(client: Client, message: any): any;
    onError(client: Client, error: any): void;
    onClose(client: Client, error: any): void;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/pro/hollaex.d.ts`.

**Classes defined**: hollaex

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 78
- Code lines: 77
- Comment lines: 51
- Blank lines: -50

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../base/ws/Client.js` (imported)
- `../base/types.js` (imported)
- `../hollaex.js` (imported)
- `../base/ws/Client.js` (referenced)
- `../base/types.js` (referenced)
- `../hollaex.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/pro/hollaex.d.ts
```

