# Documentation: js/src/pro/coinone.d.ts

## File Metadata

- **Path**: `js/src/pro/coinone.d.ts`
- **Size**: 2,893 bytes
- **Lines**: 52
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import coinoneRest from '../coinone.js';
import type { Int, Market, OrderBook, Ticker, Trade, Dict, Bool } from '../base/types.js';
import Client from '../base/ws/Client.js';
export default class coinone extends coinoneRest {
    describe(): any;
    /**
     * @method
     * @name coinone#watchOrderBook
     * @description watches information on open orders with bid (buy) and ask (sell) prices, volumes and other data
     * @see https://docs.coinone.co.kr/reference/public-websocket-orderbook
     * @param {string} symbol unified symbol of the market to fetch the order book for
     * @param {int} [limit] the maximum amount of order book entries to return
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @returns {object} A dictionary of [order book structures]{@link https://docs.ccxt.com/#/?id=order-book-structure} indexed by market symbols
     */
    watchOrderBook(symbol: string, limit?: Int, params?: {}): Promise<OrderBook>;
    handleOrderBook(client: any, message: any): void;
    handleDelta(bookside: any, delta: any): void;
    /**
     * @method
     * @name coinone#watchTicker
     * @description watches a price ticker, a statistical calculation with the information calculated over the past 24 hours for a specific market
     * @see https://docs.coinone.co.kr/reference/public-websocket-ticker
     * @param {string} symbol unified symbol of the market to fetch the ticker for
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @returns {object} a [ticker structure]{@link https://docs.ccxt.com/#/?id=ticker-structure}
     */
    watchTicker(symbol: string, params?: {}): Promise<Ticker>;
    handleTicker(client: Client, message: any): void;
    parseWsTicker(ticker: any, market?: Market): Ticker;
    /**
     * @method
     * @name coinone#watchTrades
     * @description watches information on multiple trades made in a market
     * @see https://docs.coinone.co.kr/reference/public-websocket-trade
     * @param {string} symbol unified market symbol of the market trades were made in
     * @param {int} [since] the earliest time in ms to fetch trades for
     * @param {int} [limit] the maximum number of trade structures to retrieve
     * @param {object} [params] extra parameters specific to the exchange API endpoint
     * @returns {object[]} a list of [trade structures]{@link https://docs.ccxt.com/#/?id=trade-structure}
     */
    watchTrades(symbol: string, since?: Int, limit?: Int, params?: {}): Promise<Trade[]>;
    handleTrades(client: Client, message: any): void;
    parseWsTrade(trade: Dict, market?: Market): Trade;
    handleErrorMessage(client: Client, message: any): Bool;
    handleMessage(client: Client, message: any): void;
    ping(client: Client): {
        request_type: string;
    };
    handlePong(client: Client, message: any): any;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/pro/coinone.d.ts`.

**Classes defined**: coinone

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 51
- Comment lines: 30
- Blank lines: -29

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../base/ws/Client.js` (imported)
- `../base/types.js` (imported)
- `../coinone.js` (imported)
- `../base/ws/Client.js` (referenced)
- `../base/types.js` (referenced)
- `../coinone.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/pro/coinone.d.ts
```

