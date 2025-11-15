# Documentation: ts/src/static_dependencies/messagepack/msgpack.d.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/messagepack/msgpack.d.ts`
- **Size**: 1,278 bytes
- **Lines**: 28
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/**
 * Serializes a value to a MessagePack byte array.
 * @param data The value to serialize. This can be a scalar, array or object, but not a function.
 * @param options An object that defined additional options.
 */
export function serialize(
    data: any,
    options?: {
        /** Indicates whether multiple values in data are concatenated to multiple MessagePack arrays. If undefined, the default is `false`. */
        multiple?: boolean,
        /** The value that is used to replace values of unsupported types, or a function that returns such a value, given the original value as parameter. */
        invalidTypeReplacement?: ((value: any) => (boolean | number | string | [] | object | null)) | boolean | number | string | [] | object | null,
    }): Uint8Array;

/**
 * Deserializes a MessagePack byte array to a value.
 * @param array The MessagePack byte array to deserialize.
 * @param options An object that defined additional options.
 */
export function deserialize(
    array: Uint8Array | ArrayBuffer | [],
    options?: {
		/** Indicates whether multiple concatenated MessagePack arrays are returned as an array. If undefined, the default is `false`. */
		multiple?: boolean,
    }): any;

export { serialize as encode };
export { deserialize as decode };
```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/messagepack/msgpack.d.ts`.

**Functions defined**: that, deserialize, serialize

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 26
- Comment lines: 13
- Blank lines: -11

### Main Components

**Functions** (3):
- `deserialize()`
- `serialize()`
- `that()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/messagepack/msgpack.d.ts
```

