# Documentation: ts/src/static_dependencies/ethers/utils/properties.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/ethers/utils/properties.ts`
- **Size**: 1,728 bytes
- **Lines**: 61
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/**
 *  Property helper functions.
 *
 *  @_subsection api/utils:Properties  [about-properties]
 */

function checkType(value: any, type: string, name: string): void {
    const types = type.split("|").map(t => t.trim());
    for (let i = 0; i < types.length; i++) {
        switch (type) {
            case "any":
                return;
            case "bigint":
            case "boolean":
            case "number":
            case "string":
                if (typeof(value) === type) { return; }
        }
    }

    const error: any = new Error(`invalid value for type ${ type }`);
    error.code = "INVALID_ARGUMENT";
    error.argument = `value.${ name }`;
    error.value = value;

    throw error;
}

/**
 *  Resolves to a new object that is a copy of %%value%%, but with all
 *  values resolved.
 */
export async function resolveProperties<T>(value: { [ P in keyof T ]: T[P] | Promise<T[P]>}): Promise<T> {
    const keys = Object.keys(value);
    const results = await Promise.all(keys.map((k) => Promise.resolve(value[<keyof T>k])));
    return results.reduce((accum: any, v, index) => {
        accum[keys[index]] = v;
        return accum;
    }, <{ [ P in keyof T]: T[P] }>{ });
}

/**
 *  Assigns the %%values%% to %%target%% as read-only values.
 *
 *  It %%types%% is specified, the values are checked.
 */
export function defineProperties<T>(
 target: T,
 values: { [ K in keyof T ]?: T[K] },
 types?: { [ K in keyof T ]?: string }): void {

    for (let key in values) {
        let value = values[key];

        const type = (types ? types[key]: null);
        if (type) { checkType(value, type, key); }

        Object.defineProperty(target, key, { enumerable: true, value, writable: false });
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/ethers/utils/properties.ts`.

**Functions defined**: defineProperties, checkType, resolveProperties

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 52
- Comment lines: 14
- Blank lines: -5

### Main Components

**Functions** (3):
- `checkType()`
- `defineProperties()`
- `resolveProperties()`



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
ts-node ts/src/static_dependencies/ethers/utils/properties.ts
```

