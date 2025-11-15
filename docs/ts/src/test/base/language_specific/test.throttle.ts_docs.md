# Documentation: ts/src/test/base/language_specific/test.throttle.ts

## File Metadata

- **Path**: `ts/src/test/base/language_specific/test.throttle.ts`
- **Size**: 2,543 bytes
- **Lines**: 101
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/* eslint-disable */
import { Throttler } from '../../../base/functions/throttle.js'

function testThrottle () {

    const delta = 10
    const testCases = [
        {
            'tokens': 0,
            'refillRate': 1 / 50,
            'cost': 1,
            'runs': 100,
        },
        {
            'tokens': 20,
            'refillRate': 1 / 50,
            'cost': 1,
            'runs': 100,
        },
        {
            'tokens': 40,
            'refillRate': 1 / 50,
            'cost': 1,
            'runs': 100,
        },
        {
            'tokens': 0,
            'refillRate': 1 / 20,
            'cost': 1,
            'runs': 100,
        },
        {
            'tokens': 100,
            'refillRate': 1 / 20,
            'cost': 5,
            'runs': 50,
        },
        {
            'tokens': 0,
            'refillRate': 1 / 40,
            'cost': 2,
            'runs': 50,
        },
        {
            'tokens': 1,
            'refillRate': 1 / 100,
            'cost': 1,
            'runs': 10,
        },
        {
            'tokens': 5,
            'refillRate': 1 / 100,
            'cost': 1,
            'runs': 10,
        },
        {
            'tokens': 0,
            'refillRate': 1 / 500,
            'cost': 1,
            'runs': 10,
        },
        {
            'tokens': 0,
            'refillRate': 1 / 10,
            'cost': 1,
            'runs': 500,
        },
    ]


    let number = 0
    for (const test of testCases) {
        test['number'] = number++
        const instantlyComplete = test['tokens'] / test['cost']
        // after that each run will take cost and the total time will be runs * cost / refillRate
        const remaining = test['runs'] - instantlyComplete - 1
        test['expected'] = remaining * test['cost'] / test['refillRate']
    }

    async function runner (test) {
        const throttler = new Throttler ({
            'refillRate': test['refillRate'],
            'tokens': test['tokens'],
        })
        const start = performance.now ()
        for (let i = 0; i < test['runs']; i++) {
            await throttler.throttle (test['cost'])
        }
        const end = performance.now ()
        const elapsed = end - start
        const result = Math.abs (elapsed - test['expected']) < delta
        console.log (`case ${test['number']} ${result ? 'suceeded' : 'failed'} in ${elapsed}ms expected ${test['expected']}ms`)
    }

    for (const test of testCases) {
        runner (test)
    }
}

export default testThrottle;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/base/language_specific/test.throttle.ts`.

**Functions defined**: runner, testThrottle

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 101
- Code lines: 92
- Comment lines: 2
- Blank lines: 7

### Main Components

**Functions** (2):
- `runner()`
- `testThrottle()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../base/functions/throttle.js` (imported)
- `../../../base/functions/throttle.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/base/language_specific/test.throttle.ts
```

