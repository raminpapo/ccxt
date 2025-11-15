# Documentation: examples/js/binance-server-time.js

## File Metadata

- **Path**: `examples/js/binance-server-time.js`
- **Size**: 1,276 bytes
- **Lines**: 35
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript

import ccxt from '../../js/ccxt.js';
import ololog from 'ololog'

const log  = ololog.configure ({ locate: false })

const binance = new ccxt['binance'] ()
const recvWindow = binance.options.recvWindow
const aheadWindow = 1000

async function test () {
    const localStartTime = Date.now ()
    const { serverTime } = await binance.publicGetTime ()
    const localFinishTime = Date.now ()
    const estimatedLandingTime = (localFinishTime + localStartTime) / 2

    const diff = serverTime - estimatedLandingTime

    log (`request departure time:     ${binance.iso8601 (localStartTime)}`)
    log (`response arrival time:      ${binance.iso8601 (localFinishTime)}`)
    log (`server time:                ${binance.iso8601 (serverTime)}`)
    log (`request landing time (est): ${binance.iso8601 (estimatedLandingTime)}, ${Math.abs (diff)} ms ${Math.sign (diff) > 0 ? 'behind' : 'ahead of'} server`)
    log ('\n')

    if (diff < -aheadWindow) {
        log.error.red (`your request will likely be rejected if local time is ahead of the server's time for more than ${aheadWindow} ms \n`)
    }

    if (diff > recvWindow) {
        log.error.red (`your request will likely be rejected if local time is behind server time for more than ${recvWindow} ms\n`)
    }
}

test ();

```

## High-Level Overview

This is a JavaScript file located at `examples/js/binance-server-time.js`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 25
- Comment lines: 0
- Blank lines: 10

### Main Components

**Functions** (1):
- `test()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `ololog` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/binance-server-time.js
```

