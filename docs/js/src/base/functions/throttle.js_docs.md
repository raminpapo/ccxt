# Documentation: js/src/base/functions/throttle.js

## File Metadata

- **Path**: `js/src/base/functions/throttle.js`
- **Size**: 2,198 bytes
- **Lines**: 62
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
//@ts-nocheck
/*  ------------------------------------------------------------------------ */
import { now, sleep } from './time.js';
/*  ------------------------------------------------------------------------ */
class Throttler {
    constructor(config) {
        this.config = {
            'refillRate': 1.0,
            'delay': 0.001,
            'capacity': 1.0,
            'maxCapacity': 2000,
            'tokens': 0,
            'cost': 1.0,
        };
        Object.assign(this.config, config);
        this.queue = [];
        this.running = false;
    }
    async loop() {
        let lastTimestamp = now();
        while (this.running) {
            const { resolver, cost } = this.queue[0];
            if (this.config['tokens'] >= 0) {
                this.config['tokens'] -= cost;
                resolver();
                this.queue.shift();
                // contextswitch
                await Promise.resolve();
                if (this.queue.length === 0) {
                    this.running = false;
                }
            }
            else {
                await sleep(this.config['delay'] * 1000);
                const current = now();
                const elapsed = current - lastTimestamp;
                lastTimestamp = current;
                const tokens = this.config['tokens'] + (this.config['refillRate'] * elapsed);
                this.config['tokens'] = Math.min(tokens, this.config['capacity']);
            }
        }
    }
    throttle(cost = undefined) {
        let resolver;
        const promise = new Promise((resolve, reject) => {
            resolver = resolve;
        });
        if (this.queue.length > this.config['maxCapacity']) {
            throw new Error('throttle queue is over maxCapacity (' + this.config['maxCapacity'].toString() + '), see https://docs.ccxt.com/#/README?id=maximum-requests-capacity');
        }
        cost = (cost === undefined) ? this.config['cost'] : cost;
        this.queue.push({ resolver, cost });
        if (!this.running) {
            this.running = true;
            this.loop();
        }
        return promise;
    }
}
export { Throttler, };
// ----------------------------------------

```

## High-Level Overview

This is a JavaScript file located at `js/src/base/functions/throttle.js`.

**Classes defined**: Throttler

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 62
- Code lines: 58
- Comment lines: 5
- Blank lines: -1

### Main Components

**Classes** (1):
- `Throttler`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./time.js` (imported)
- `./time.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/base/functions/throttle.js
```

