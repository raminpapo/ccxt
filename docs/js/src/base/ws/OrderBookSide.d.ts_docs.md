# Documentation: js/src/base/ws/OrderBookSide.d.ts

## File Metadata

- **Path**: `js/src/base/ws/OrderBookSide.d.ts`
- **Size**: 1,344 bytes
- **Lines**: 41
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
interface IOrderBookSide<T> extends Array<T> {
    store(price: any, size: any): any;
    storeArray(array: any[]): any;
    limit(): any;
}
declare class OrderBookSide extends Array implements IOrderBookSide<any> {
    constructor(deltas?: any[], depth?: any);
    storeArray(delta: any): void;
    store(price: any, size: any): void;
    limit(): void;
}
declare class CountedOrderBookSide extends OrderBookSide {
    store(price: any, size: any): void;
    storeArray(delta: any): void;
}
declare class IndexedOrderBookSide extends Array implements IOrderBookSide<any> {
    constructor(deltas?: any[], depth?: number);
    store(price: any, size: any): void;
    storeArray(delta: any): void;
    limit(): void;
}
declare class Asks extends OrderBookSide {
    get side(): boolean;
}
declare class Bids extends OrderBookSide {
    get side(): boolean;
}
declare class CountedAsks extends CountedOrderBookSide {
    get side(): boolean;
}
declare class CountedBids extends CountedOrderBookSide {
    get side(): boolean;
}
declare class IndexedAsks extends IndexedOrderBookSide {
    get side(): boolean;
}
declare class IndexedBids extends IndexedOrderBookSide {
    get side(): boolean;
}
export { Asks, Bids, OrderBookSide, CountedAsks, CountedBids, CountedOrderBookSide, IndexedAsks, IndexedBids, IndexedOrderBookSide, IOrderBookSide };

```

## High-Level Overview

This is a TypeScript file located at `js/src/base/ws/OrderBookSide.d.ts`.

**Classes defined**: Bids, CountedOrderBookSide, IndexedBids, IndexedOrderBookSide, Asks, CountedBids, OrderBookSide, IndexedAsks, CountedAsks



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 40
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/base/ws/OrderBookSide.d.ts
```

