# Documentation: ts/src/static_dependencies/starknet/utils/calldata/tuple.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/utils/calldata/tuple.ts`
- **Size**: 3,177 bytes
- **Lines**: 117
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/* eslint-disable no-plusplus */
import { isCairo1Type, isTypeNamedTuple } from './cairo.js';

function parseNamedTuple(namedTuple: string): any {
  const name = namedTuple.substring(0, namedTuple.indexOf(':'));
  const type = namedTuple.substring(name.length + ':'.length);
  return { name, type };
}

function parseSubTuple(s: string) {
  if (!s.includes('(')) return { subTuple: [], result: s };
  const subTuple: string[] = [];
  let result = '';
  let i = 0;
  while (i < s.length) {
    if (s[i] === '(') {
      let counter = 1;
      const lBracket = i;
      i++;
      while (counter) {
        if (s[i] === ')') counter--;
        if (s[i] === '(') counter++;
        i++;
      }
      subTuple.push(s.substring(lBracket, i));
      result += ' ';
      i--;
    } else {
      result += s[i];
    }
    i++;
  }

  return {
    subTuple,
    result,
  };
}

function extractCairo0Tuple(type: string) {
  const cleanType = type.replace(/\s/g, '').slice(1, -1); // remove first lvl () and spaces

  // Decompose subTuple
  const { subTuple, result } = parseSubTuple(cleanType);

  // Recompose subTuple
  let recomposed = result.split(',').map((it) => {
    return subTuple.length ? it.replace(' ', subTuple.shift() as string) : it;
  });

  // Parse named tuple
  if (isTypeNamedTuple(type)) {
    recomposed = recomposed.reduce((acc, it) => {
      return acc.concat(parseNamedTuple(it));
    }, []);
  }

  return recomposed;
}

function getClosureOffset(input: string, open: string, close: string): number {
  for (let i = 0, counter = 0; i < input.length; i++) {
    if (input[i] === open) {
      counter++;
    } else if (input[i] === close && --counter === 0) {
      return i;
    }
  }
  return Number.POSITIVE_INFINITY;
}

function extractCairo1Tuple(type: string): string[] {
  // un-named tuples support
  const input = type.slice(1, -1); // remove first lvl ()
  const result: string[] = [];

  let currentIndex: number = 0;
  let limitIndex: number;

  while (currentIndex < input.length) {
    switch (true) {
      // Tuple
      case input[currentIndex] === '(': {
        limitIndex = currentIndex + getClosureOffset(input.slice(currentIndex), '(', ')') + 1;
        break;
      }
      case input.startsWith('core::result::Result::<', currentIndex) ||
        input.startsWith('core::array::Array::<', currentIndex) ||
        input.startsWith('core::option::Option::<', currentIndex): {
        limitIndex = currentIndex + getClosureOffset(input.slice(currentIndex), '<', '>') + 1;
        break;
      }
      default: {
        const commaIndex = input.indexOf(',', currentIndex);
        limitIndex = commaIndex !== -1 ? commaIndex : Number.POSITIVE_INFINITY;
      }
    }

    result.push(input.slice(currentIndex, limitIndex));
    currentIndex = limitIndex + 2; // +2 to skip ', '
  }

  return result;
}

/**
 * Convert tuple string definition into object like definition
 * @param type tuple string definition
 * @returns object like tuple
 */
export default function extractTupleMemberTypes(type: string): (string | object)[] {
  if (isCairo1Type(type)) {
    return extractCairo1Tuple(type);
  }
  return extractCairo0Tuple(type);
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/utils/calldata/tuple.ts`.

**Functions defined**: extractCairo1Tuple, extractTupleMemberTypes, parseSubTuple, parseNamedTuple, getClosureOffset, extractCairo0Tuple

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 117
- Code lines: 96
- Comment lines: 11
- Blank lines: 10

### Main Components

**Functions** (6):
- `extractCairo0Tuple()`
- `extractCairo1Tuple()`
- `extractTupleMemberTypes()`
- `getClosureOffset()`
- `parseNamedTuple()`
- `parseSubTuple()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./cairo.js` (imported)
- `./cairo.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/starknet/utils/calldata/tuple.ts
```

