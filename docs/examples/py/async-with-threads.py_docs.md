# Documentation: examples/py/async-with-threads.py

## File Metadata

- **Path**: `examples/py/async-with-threads.py`
- **Size**: 876 bytes
- **Lines**: 39
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import threading
import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402


async def test(loop):
    exchange = ccxt.bittrex({
        'asyncio_loop': loop,
    })
    print(await exchange.fetch_ticker('ETH/BTC'))
    await exchange.close()


def function_in_a_thread():
    # get_event_loop doesn't work inside a thread
    loop = asyncio.new_event_loop()
    loop.run_until_complete(test(loop))


def another_threaded_function():
    global_loop.run_until_complete(test(global_loop))


global_loop = asyncio.get_event_loop()
thread = threading.Thread(target=function_in_a_thread)
thread2 = threading.Thread(target=another_threaded_function)
thread.start()
thread2.start()
thread.join()
thread2.join()

```

## High-Level Overview

This is a Python file located at `examples/py/async-with-threads.py`.

**Functions defined**: test, another_threaded_function, function_in_a_thread

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 25
- Comment lines: 2
- Blank lines: 12

### Main Components

**Functions** (3):
- `another_threaded_function()`
- `function_in_a_thread()`
- `test()`



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
python examples/py/async-with-threads.py
```

