# Documentation: python/ccxt/async_support/base/throttler.py

## File Metadata

- **Path**: `python/ccxt/async_support/base/throttler.py`
- **Size**: 1,841 bytes
- **Lines**: 51
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import asyncio
import collections
from time import time


class Throttler:
    def __init__(self, config, loop=None):
        self.loop = loop
        self.config = {
            'refillRate': 1.0,
            'delay': 0.001,
            'cost': 1.0,
            'tokens': 0,
            'maxCapacity': 2000,
            'capacity': 1.0,
        }
        self.config.update(config)
        self.queue = collections.deque()
        self.running = False

    async def looper(self):
        last_timestamp = time() * 1000
        while self.running:
            future, cost = self.queue[0]
            cost = self.config['cost'] if cost is None else cost
            if self.config['tokens'] >= 0:
                self.config['tokens'] -= cost
                if not future.done():
                    future.set_result(None)
                self.queue.popleft()
                # context switch
                await asyncio.sleep(0)
                if len(self.queue) == 0:
                    self.running = False
            else:
                await asyncio.sleep(self.config['delay'])
                now = time() * 1000
                elapsed = now - last_timestamp
                last_timestamp = now
                self.config['tokens'] = min(self.config['tokens'] + elapsed * self.config['refillRate'], self.config['capacity'])

    def __call__(self, cost=None):
        future = asyncio.Future()
        if len(self.queue) > self.config['maxCapacity']:
            raise RuntimeError('throttle queue is over maxCapacity (' + str(int(self.config['maxCapacity'])) + '), see https://docs.ccxt.com/#/README?id=maximum-requests-capacity')
        self.queue.append((future, cost))
        if not self.running:
            self.running = True
            asyncio.ensure_future(self.looper(), loop=self.loop)
        return future

```

## High-Level Overview

This is a Python file located at `python/ccxt/async_support/base/throttler.py`.

**Classes defined**: Throttler

**Functions defined**: __call__, looper, __init__

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 51
- Code lines: 45
- Comment lines: 1
- Blank lines: 5

### Main Components

**Classes** (1):
- `Throttler`

**Functions** (3):
- `__call__()`
- `__init__()`
- `looper()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/async_support/base/throttler.py
```

