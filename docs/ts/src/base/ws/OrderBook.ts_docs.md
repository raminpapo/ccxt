# Documentation: ts/src/base/ws/OrderBook.ts

## File Metadata

- **Path**: `ts/src/base/ws/OrderBook.ts`
- **Size**: 5,339 bytes
- **Lines**: 184
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/* eslint-disable max-classes-per-file */
// @ts-nocheck

import { iso8601 } from '../../base/functions/time.js';
import { extend, deepExtend } from '../../base/functions/generic.js';

import {
    Asks,
    Bids,
    CountedAsks,
    CountedBids,
    IndexedAsks,
    IndexedBids,
    IOrderBookSide
    // IncrementalAsks,
    // IncrementalBids,
    // IncrementalIndexedAsks,
    // IncrementalIndexedBids, // check this
} from './OrderBookSide.js';
import { Int, Str } from '../types.js';

// ----------------------------------------------------------------------------
// overwrites absolute volumes at price levels

interface CustomOrderBookProp  {
    cache: any[];
}

class OrderBook implements CustomOrderBookProp {

    cache = [] // make prop visible so we use typed OrderBooks

    asks: IOrderBookSide<any>;

    bids: IOrderBookSide<any>;

    timestamp: Int;

    datetime: Str;

    nonce: Int;

    symbol: Str;

    constructor (snapshot = {}, depth = undefined) {

        Object.defineProperty (this, 'cache', {
            __proto__: null, // make it invisible
            value: [],
            writable: true,
            enumerable: false,
        })

        depth = depth || Number.MAX_SAFE_INTEGER

        const defaults = {
            'bids': [],
            'asks': [],
            'timestamp': undefined,
            'datetime': undefined,
            'nonce': undefined,
            'symbol': undefined,
        }

        // merge to this
        const entries = Object.entries (extend (defaults, snapshot))
        for (let i = 0; i < entries.length; i++) {
            const [ property, value ] = entries[i]
            this[property] = value
        }

        // wrap plain arrays with Bids/Asks classes if necessary
        if (this.asks.constructor.name === 'Array') {
            this.asks = new Asks (this.asks, depth)
        }
        if (this.bids.constructor.name === 'Array') {
            this.bids = new Bids (this.bids, depth)
        }
        if (this.timestamp) {
            this.datetime = iso8601 (this.timestamp)
        }
    }

    limit () {
        this.asks.limit ()
        this.bids.limit ()
        return this
    }

    update (snapshot) {
        if ((snapshot.nonce !== undefined) &&
            (this.nonce !== undefined) &&
            (snapshot.nonce <= this.nonce)) {
            return this
        }
        this.nonce = snapshot.nonce
        this.timestamp = snapshot.timestamp
        this.datetime = iso8601 (this.timestamp)
        return this.reset (snapshot)
    }

    reset (snapshot = {}) {
        this.asks.index.fill (Number.MAX_VALUE)
        this.asks.length = 0
        if (snapshot.asks) {
            for (let i = 0; i < snapshot.asks.length; i++) {
                this.asks.storeArray (snapshot.asks[i])
            }
        }
        this.bids.index.fill (Number.MAX_VALUE)
        this.bids.length = 0
        if (snapshot.bids) {
            for (let i = 0; i < snapshot.bids.length; i++) {
                this.bids.storeArray (snapshot.bids[i])
            }
        }
        this.nonce = snapshot.nonce
        this.timestamp = snapshot.timestamp
        this.datetime = iso8601 (this.timestamp)
        this.symbol = snapshot.symbol
        return this
    }
}

// ----------------------------------------------------------------------------
// overwrites absolute volumes at price levels
// or deletes price levels based on order counts (3rd value in a bidask delta)

class CountedOrderBook extends OrderBook {
    constructor (snapshot = {}, depth = undefined) {
        super (extend (snapshot, {
            'asks': new CountedAsks (snapshot.asks || [], depth),
            'bids': new CountedBids (snapshot.bids || [], depth),
        }))
    }
}

// ----------------------------------------------------------------------------
// indexed by order ids (3rd value in a bidask delta)

class IndexedOrderBook extends OrderBook {
    constructor (snapshot = {}, depth = undefined) {
        super (extend (snapshot, {
            'asks': new IndexedAsks (snapshot.asks || [], depth),
            'bids': new IndexedBids (snapshot.bids || [], depth),
        }))
    }
}

// ----------------------------------------------------------------------------
// adjusts the volumes by positive or negative relative changes or differences

// class IncrementalOrderBook extends OrderBook {
//     constructor (snapshot = {}, depth = undefined) {
//         super (extend (snapshot, {
//             'asks': new IncrementalAsks (snapshot.asks || [], depth),
//             'bids': new IncrementalBids (snapshot.bids || [], depth),
//         }))
//     }
// }


// // ----------------------------------------------------------------------------
// // incremental and indexed (2 in 1)

// class IncrementalIndexedOrderBook extends OrderBook {
//     constructor (snapshot = {}, depth = undefined) {
//         super (extend (snapshot, {
//             'asks': new IncrementalIndexedAsks (snapshot.asks || [], depth),
//             'bids': new IncrementalIndexedBids (snapshot.bids || [], depth),
//         }))
//     }
// }

// ----------------------------------------------------------------------------

export {
    OrderBook,
    CountedOrderBook,
    IndexedOrderBook,
    // IncrementalOrderBook,
    // IncrementalIndexedOrderBook,
};

```

## High-Level Overview

This is a TypeScript file located at `ts/src/base/ws/OrderBook.ts`.

**Classes defined**: OrderBook, IndexedOrderBook, CountedOrderBook, IncrementalIndexedOrderBook, IncrementalOrderBook

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 184
- Code lines: 114
- Comment lines: 38
- Blank lines: 32

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

- `./OrderBookSide.js` (imported)
- `../../base/functions/generic.js` (imported)
- `../../base/functions/time.js` (imported)
- `../types.js` (imported)
- `./OrderBookSide.js` (referenced)
- `../../base/functions/generic.js` (referenced)
- `../../base/functions/time.js` (referenced)
- `../types.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/base/ws/OrderBook.ts
```

