# Documentation: ts/src/static_dependencies/ethers/utils/events.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/ethers/utils/events.ts`
- **Size**: 2,810 bytes
- **Lines**: 106
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/**
 *  Events allow for applications to use the observer pattern, which
 *  allows subscribing and publishing events, outside the normal
 *  execution paths.
 *
 *  @_section api/utils/events:Events  [about-events]
 */
import { defineProperties } from "./properties.js";

/**
 *  A callback function called when a an event is triggered.
 */
export type Listener = (...args: Array<any>) => void;

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
export class EventPayload<T> {
    /**
     *  The event filter.
     */
    readonly filter!: T;

    /**
     *  The **EventEmitterable**.
     */
    readonly emitter!: EventEmitterable<T>;

    readonly #listener: null | Listener;

    /**
     *  Create a new **EventPayload** for %%emitter%% with
     *  the %%listener%% and for %%filter%%.
     */
    constructor(emitter: EventEmitterable<T>, listener: null | Listener, filter: T) {
        this.#listener = listener;
        defineProperties<EventPayload<any>>(this, { emitter, filter });
    }

    /**
     *  Unregister the triggered listener for future events.
     */
    async removeListener(): Promise<void> {
        if (this.#listener == null) { return; }
        await this.emitter.off(this.filter, this.#listener);
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/ethers/utils/events.ts`.

**Classes defined**: EventPayload

**Functions defined**: called

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 106
- Code lines: 90
- Comment lines: 64
- Blank lines: -48

### Main Components

**Functions** (1):
- `called()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./properties.js` (imported)
- `./properties.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/ethers/utils/events.ts
```

