# Documentation: js/src/static_dependencies/ethers/utils/events.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/utils/events.d.ts`
- **Size**: 2,274 bytes
- **Lines**: 77
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/**
 *  A callback function called when a an event is triggered.
 */
export declare type Listener = (...args: Array<any>) => void;
/**
 *  An **EventEmitterable** behaves similar to an EventEmitter
 *  except provides async access to its methods.
 *
 *  An EventEmitter implements the observer pattern.
 */
export interface EventEmitterable<T> {
    /**
     *  Registers a %%listener%% that is called whenever the
     *  %%event%% occurs until unregistered.
     */
    on(event: T, listener: Listener): Promise<this>;
    /**
     *  Registers a %%listener%% that is called the next time
     *  %%event%% occurs.
     */
    once(event: T, listener: Listener): Promise<this>;
    /**
     *  Triggers each listener for %%event%% with the %%args%%.
     */
    emit(event: T, ...args: Array<any>): Promise<boolean>;
    /**
     *  Resolves to the number of listeners for %%event%%.
     */
    listenerCount(event?: T): Promise<number>;
    /**
     *  Resolves to the listeners for %%event%%.
     */
    listeners(event?: T): Promise<Array<Listener>>;
    /**
     *  Unregister the %%listener%% for %%event%%. If %%listener%%
     *  is unspecified, all listeners are unregistered.
     */
    off(event: T, listener?: Listener): Promise<this>;
    /**
     *  Unregister all listeners for %%event%%.
     */
    removeAllListeners(event?: T): Promise<this>;
    /**
     *  Alias for [[on]].
     */
    addListener(event: T, listener: Listener): Promise<this>;
    /**
     *  Alias for [[off]].
     */
    removeListener(event: T, listener: Listener): Promise<this>;
}
/**
 *  When an [[EventEmitterable]] triggers a [[Listener]], the
 *  callback always ahas one additional argument passed, which is
 *  an **EventPayload**.
 */
export declare class EventPayload<T> {
    #private;
    /**
     *  The event filter.
     */
    readonly filter: T;
    /**
     *  The **EventEmitterable**.
     */
    readonly emitter: EventEmitterable<T>;
    /**
     *  Create a new **EventPayload** for %%emitter%% with
     *  the %%listener%% and for %%filter%%.
     */
    constructor(emitter: EventEmitterable<T>, listener: null | Listener, filter: T);
    /**
     *  Unregister the triggered listener for future events.
     */
    removeListener(): Promise<void>;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/ethers/utils/events.d.ts`.

**Classes defined**: EventPayload

**Functions defined**: called

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 77
- Code lines: 75
- Comment lines: 58
- Blank lines: -56

### Main Components

**Functions** (1):
- `called()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/ethers/utils/events.d.ts
```

