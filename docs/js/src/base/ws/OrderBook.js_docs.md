# Documentation: js/src/base/ws/OrderBook.js

## File Metadata

- **Path**: `js/src/base/ws/OrderBook.js`
- **Size**: 4,711 bytes
- **Lines**: 125
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
/* eslint-disable max-classes-per-file */
// @ts-nocheck
import { iso8601 } from '../../base/functions/time.js';
import { extend } from '../../base/functions/generic.js';
import { Asks, Bids, CountedAsks, CountedBids, IndexedAsks, IndexedBids } from './OrderBookSide.js';
class OrderBook {
    constructor(snapshot = {}, depth = undefined) {
        this.cache = []; // make prop visible so we use typed OrderBooks
        Object.defineProperty(this, 'cache', {
            __proto__: null,
            value: [],
            writable: true,
            enumerable: false,
        });
        depth = depth || Number.MAX_SAFE_INTEGER;
        const defaults = {
            'bids': [],
            'asks': [],
            'timestamp': undefined,
            'datetime': undefined,
            'nonce': undefined,
            'symbol': undefined,
        };
        // merge to this
        const entries = Object.entries(extend(defaults, snapshot));
        for (let i = 0; i < entries.length; i++) {
            const [property, value] = entries[i];
            this[property] = value;
        }
        // wrap plain arrays with Bids/Asks classes if necessary
        if (this.asks.constructor.name === 'Array') {
            this.asks = new Asks(this.asks, depth);
        }
        if (this.bids.constructor.name === 'Array') {
            this.bids = new Bids(this.bids, depth);
        }
        if (this.timestamp) {
            this.datetime = iso8601(this.timestamp);
        }
    }
    limit() {
        this.asks.limit();
        this.bids.limit();
        return this;
    }
    update(snapshot) {
        if ((snapshot.nonce !== undefined) &&
            (this.nonce !== undefined) &&
            (snapshot.nonce <= this.nonce)) {
            return this;
        }
        this.nonce = snapshot.nonce;
        this.timestamp = snapshot.timestamp;
        this.datetime = iso8601(this.timestamp);
        return this.reset(snapshot);
    }
    reset(snapshot = {}) {
        this.asks.index.fill(Number.MAX_VALUE);
        this.asks.length = 0;
        if (snapshot.asks) {
            for (let i = 0; i < snapshot.asks.length; i++) {
                this.asks.storeArray(snapshot.asks[i]);
            }
        }
        this.bids.index.fill(Number.MAX_VALUE);
        this.bids.length = 0;
        if (snapshot.bids) {
            for (let i = 0; i < snapshot.bids.length; i++) {
                this.bids.storeArray(snapshot.bids[i]);
            }
        }
        this.nonce = snapshot.nonce;
        this.timestamp = snapshot.timestamp;
        this.datetime = iso8601(this.timestamp);
        this.symbol = snapshot.symbol;
        return this;
    }
}
// ----------------------------------------------------------------------------
// overwrites absolute volumes at price levels
// or deletes price levels based on order counts (3rd value in a bidask delta)
class CountedOrderBook extends OrderBook {
    constructor(snapshot = {}, depth = undefined) {
        super(extend(snapshot, {
            'asks': new CountedAsks(snapshot.asks || [], depth),
            'bids': new CountedBids(snapshot.bids || [], depth),
        }));
    }
}
// ----------------------------------------------------------------------------
// indexed by order ids (3rd value in a bidask delta)
class IndexedOrderBook extends OrderBook {
    constructor(snapshot = {}, depth = undefined) {
        super(extend(snapshot, {
            'asks': new IndexedAsks(snapshot.asks || [], depth),
            'bids': new IndexedBids(snapshot.bids || [], depth),
        }));
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
export { OrderBook, CountedOrderBook, IndexedOrderBook,
// IncrementalOrderBook,
// IncrementalIndexedOrderBook,
 };

```

## High-Level Overview

This is a JavaScript file located at `js/src/base/ws/OrderBook.js`.

**Classes defined**: OrderBook, IndexedOrderBook, CountedOrderBook, IncrementalIndexedOrderBook, IncrementalOrderBook

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 125
- Code lines: 93
- Comment lines: 32
- Blank lines: 0

### Main Components

**Classes** (1):
- `OrderBook`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

- `./OrderBookSide.js` (imported)
- `../../base/functions/generic.js` (imported)
- `../../base/functions/time.js` (imported)
- `./OrderBookSide.js` (referenced)
- `../../base/functions/generic.js` (referenced)
- `../../base/functions/time.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/base/ws/OrderBook.js
```

