# Documentation: js/src/base/ws/OrderBook.d.ts

## File Metadata

- **Path**: `js/src/base/ws/OrderBook.d.ts`
- **Size**: 740 bytes
- **Lines**: 26
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { IOrderBookSide } from './OrderBookSide.js';
import { Int, Str } from '../types.js';
interface CustomOrderBookProp {
    cache: any[];
}
declare class OrderBook implements CustomOrderBookProp {
    cache: any[];
    asks: IOrderBookSide<any>;
    bids: IOrderBookSide<any>;
    timestamp: Int;
    datetime: Str;
    nonce: Int;
    symbol: Str;
    constructor(snapshot?: {}, depth?: any);
    limit(): this;
    update(snapshot: any): this;
    reset(snapshot?: {}): this;
}
declare class CountedOrderBook extends OrderBook {
    constructor(snapshot?: {}, depth?: any);
}
declare class IndexedOrderBook extends OrderBook {
    constructor(snapshot?: {}, depth?: any);
}
export { OrderBook, CountedOrderBook, IndexedOrderBook, };

```

## High-Level Overview

This is a TypeScript file located at `js/src/base/ws/OrderBook.d.ts`.

**Classes defined**: OrderBook, IndexedOrderBook, CountedOrderBook

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 25
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

- `./OrderBookSide.js` (imported)
- `../types.js` (imported)
- `./OrderBookSide.js` (referenced)
- `../types.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/base/ws/OrderBook.d.ts
```

