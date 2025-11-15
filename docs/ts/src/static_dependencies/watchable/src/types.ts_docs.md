# Documentation: ts/src/static_dependencies/watchable/src/types.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/watchable/src/types.ts`
- **Size**: 1,710 bytes
- **Lines**: 56
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/** TYPES */

/** A promise that exploits a single, memory-safe upstream subscription
 * to a single re-used Unpromise that persists for the VM lifetime of a
 * Promise.
 *
 * Calling unsubscribe() removes the subscription, eliminating
 * all references to the SubscribedPromise. */
export interface SubscribedPromise<T> extends Promise<T> {
  unsubscribe: () => void;
}

/** Duplicate of Promise interface, except each call returns SubscribedPromise */
export interface ProxyPromise<T> extends Promise<T> {
  subscribe: () => SubscribedPromise<T>;

  then: <TResult1 = T, TResult2 = never>(
    onfulfilled?:
      | ((value: T) => TResult1 | PromiseLike<TResult1>)
      | null
      | undefined,
    onrejected?:
      | ((reason: any) => TResult2 | PromiseLike<TResult2>)
      | null
      | undefined
  ) => SubscribedPromise<TResult1 | TResult2>;

  catch: <TResult = never>(
    onrejected?:
      | ((reason: any) => TResult | PromiseLike<TResult>)
      | null
      | undefined
  ) => SubscribedPromise<T | TResult>;

  finally: (
    onfinally?: (() => void) | null | undefined
  ) => SubscribedPromise<T>;
}

export type PromiseExecutor<T> = (
  resolve: (value: T | PromiseLike<T>) => void,
  reject: (reason?: any) => void
) => void;

/** A standard pattern for a resolvable, rejectable Promise, based
 * on the emerging ES2023 standard. Type ported from
 * https://github.com/microsoft/TypeScript/pull/56593 */
export interface PromiseWithResolvers<T> {
  promise: Promise<T>;
  resolve: (value: T | PromiseLike<T>) => void;
  reject: (reason?: any) => void;
}

/** Given an array, this is the union of its members' types. */
export type MemberOf<Arr extends readonly unknown[]> = Arr[number];

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/watchable/src/types.ts`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 47
- Comment lines: 12
- Blank lines: -3

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
ts-node ts/src/static_dependencies/watchable/src/types.ts
```

