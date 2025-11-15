# Documentation: js/src/pro/luno.d.ts

## File Metadata

- **Path**: `js/src/pro/luno.d.ts`
- **Size**: 2,545 bytes
- **Lines**: 45
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import lunoRest from '../luno.js';
import type { Int, Trade, OrderBook, IndexType } from '../base/types.js';
import Client from '../base/ws/Client.js';
export default class luno extends lunoRest {
    describe(): any;
    /**
     * @method
     * @name luno#watchTrades
     * @description get the list of most recent trades for a particular symbol
     * @see https://www.luno.com/en/developers/api#tag/Streaming-API
     * @param {string} symbol unified symbol of the market to fetch trades for
     * @param {int} [since] timestamp in ms of the earliest trade to fetch
     * @param {int} [limit] the maximum amount of    trades to fetch
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @returns {object[]} a list of [trade structures]{@link https://docs.ccxt.com/#/?id=public-trades}
     */
    watchTrades(symbol: string, since?: Int, limit?: Int, params?: {}): Promise<Trade[]>;
    handleTrades(client: Client, message: any, subscription: any): void;
    parseTrade(trade: any, market?: any): Trade;
    /**
     * @method
     * @name luno#watchOrderBook
     * @description watches information on open orders with bid (buy) and ask (sell) prices, volumes and other data
     * @param {string} symbol unified symbol of the market to fetch the order book for
     * @param {int} [limit] the maximum amount of order book entries to return
     * @param {objectConstructor} [params] extra parameters specific to the exchange API endpoint
     * @param {string} [params.type] accepts l2 or l3 for level 2 or level 3 order book
     * @returns {object} A dictionary of [order book structures]{@link https://docs.ccxt.com/#/?id=order-book-structure} indexed by market symbols
     */
    watchOrderBook(symbol: string, limit?: Int, params?: {}): Promise<OrderBook>;
    handleOrderBook(client: Client, message: any, subscription: any): void;
    customParseOrderBook(orderbook: any, symbol: any, timestamp?: any, bidsKey?: string, asksKey?: IndexType, priceKey?: IndexType, amountKey?: IndexType, countOrIdKey?: IndexType): {
        symbol: any;
        bids: any[];
        asks: any[];
        timestamp: any;
        datetime: string;
        nonce: any;
    };
    parseBidsAsks(bidasks: any, priceKey?: IndexType, amountKey?: IndexType, thirdKey?: IndexType): any[];
    customParseBidAsk(bidask: any, priceKey?: IndexType, amountKey?: IndexType, thirdKey?: IndexType): number[];
    handleDelta(orderbook: any, message: any): void;
    handleMessage(client: Client, message: any): void;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/pro/luno.d.ts`.

**Classes defined**: luno

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 44
- Comment lines: 21
- Blank lines: -20

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../base/ws/Client.js` (imported)
- `../base/types.js` (imported)
- `../luno.js` (imported)
- `../base/ws/Client.js` (referenced)
- `../base/types.js` (referenced)
- `../luno.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/pro/luno.d.ts
```

