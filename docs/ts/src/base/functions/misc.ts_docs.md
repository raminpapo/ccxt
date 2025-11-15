# Documentation: ts/src/base/functions/misc.ts

## File Metadata

- **Path**: `ts/src/base/functions/misc.ts`
- **Size**: 3,587 bytes
- **Lines**: 114
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

import { ROUND_UP, ROUND_DOWN } from './number.js'
import { asFloat } from './type.js'
import { NotSupported } from '../errors.js'
import { Dictionary, Num } from '../types.js'

//-------------------------------------------------------------------------
// converts timeframe to seconds
const parseTimeframe = (timeframe: string): number => {

    const amount = asFloat (timeframe.slice (0, -1));
    const unit = timeframe.slice (-1);
    let scale: Num = undefined;

    if (unit === 'y') {
        scale = 60 * 60 * 24 * 365;
    } else if (unit === 'M') {
        scale = 60 * 60 * 24 * 30;
    } else if (unit === 'w') {
        scale = 60 * 60 * 24 * 7;
    } else if (unit === 'd') {
        scale = 60 * 60 * 24;
    } else if (unit === 'h') {
        scale = 60 * 60;
    } else if (unit === 'm') {
        scale = 60;
    } else if (unit === 's') {
        scale = 1;
    } else {
        throw new NotSupported ('timeframe unit ' + unit + ' is not supported');
    }

    return amount * scale;
};

const roundTimeframe = (timeframe: string, timestamp: number, direction = ROUND_DOWN) => {
    const ms = parseTimeframe (timeframe) * 1000;
    // Get offset based on timeframe in milliseconds
    const offset = timestamp % ms;
    return timestamp - offset + ((direction === ROUND_UP) ? ms : 0);
};

const extractParams = (string: string): string[] => {
    /**
     * @ignore
     * @method
     * @param string usually a url path
     * @returns {[string]} all substrings surrounded by {} from parameter string
     */
    const re = /{([\w-]+)}/g;
    const matches = [];
    let match = re.exec (string);
    while (match) {
        matches.push (match[1]);
        match = re.exec (string);
    }
    return matches;
};

const implodeParams = (string: string, params: Dictionary<any> | any[]): string => {
    if (!Array.isArray (params)) {
        const keys = Object.keys (params);
        for (let i = 0; i < keys.length; i++) {
            const key = keys[i];
            if (!Array.isArray (params[key])) {
                string = string.replace ('{' + key + '}', params[key]);
            }
        }
    }
    return string;
};

function vwap (baseVolume: number, quoteVolume: number): Num {
    return ((baseVolume !== undefined) && (quoteVolume !== undefined) && (baseVolume > 0)) ? (quoteVolume / baseVolume) : undefined;
}

/*  ------------------------------------------------------------------------ */

function aggregate (bidasks) {  // TODO: Parameter 'bidasks' implicitly has an 'any' type.ts(7006)

    const result = {}

    for (let i = 0; i < bidasks.length; i++) {
        const [ price, volume ] = bidasks[i];
        if (volume > 0) {
            result[price] = (result[price] || 0) + volume  // TODO: Element implicitly has an 'any' type because expression of type 'any' can't be used to index type '{}'.ts(7053)
        }
    }

    return Object.keys (result).map ((price) => [parseFloat (price), parseFloat (result[price])])  // TODO: Element implicitly has an 'any' type because expression of type 'string' can't be used to index type '{}',   No index signature with a parameter of type 'string' was found on type '{}'.ts(7053)
}

function selfIsDefined () {
    let selfIsDefined = false
    try {
        selfIsDefined = self !== undefined
    } catch (e) {
        selfIsDefined = false
    }
    return selfIsDefined
}

export {
    aggregate,
    parseTimeframe,
    roundTimeframe,
    implodeParams,
    extractParams,
    vwap,
    selfIsDefined
}

/*  ------------------------------------------------------------------------ */

```

## High-Level Overview

This is a TypeScript file located at `ts/src/base/functions/misc.ts`.

**Functions defined**: selfIsDefined, vwap, aggregate

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 114
- Code lines: 93
- Comment lines: 11
- Blank lines: 10

### Main Components

**Functions** (3):
- `aggregate()`
- `selfIsDefined()`
- `vwap()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../errors.js` (imported)
- `../types.js` (imported)
- `./type.js` (imported)
- `./number.js` (imported)
- `../errors.js` (referenced)
- `../types.js` (referenced)
- `./type.js` (referenced)
- `./number.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/base/functions/misc.ts
```

