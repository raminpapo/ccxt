# Documentation: python/ccxt/async_support/base/ws/future.py

## File Metadata

- **Path**: `python/ccxt/async_support/base/ws/future.py`
- **Size**: 1,450 bytes
- **Lines**: 47
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import asyncio

# Test by running:
# - python python/ccxt/pro/test/base/test_close.py
# - python python/ccxt/pro/test/base/test_future.py
class Future(asyncio.Future):

    def resolve(self, result=None):
        if not self.done():
            self.set_result(result)

    def reject(self, error=None):
        if not self.done():
            self.set_exception(error)

    @classmethod
    def race(cls, futures):
        future = Future()
        coro = asyncio.wait(futures, return_when=asyncio.FIRST_COMPLETED)
        task = asyncio.create_task(coro)

        def callback(done):
            complete, _ = done.result()
            # check for exceptions
            exceptions = []
            cancelled = False
            for f in complete:
                if f.cancelled():
                    cancelled = True
                else:
                    err = f.exception()
                    if err:
                        exceptions.append(err)
            # if any exceptions return with first exception
            if future.cancelled():
                return
            if len(exceptions) > 0:
                future.set_exception(exceptions[0])
            # else return first result
            elif cancelled:
                future.cancel()
            else:
                first_result = list(complete)[0].result()
                future.set_result(first_result)
        task.add_done_callback(callback)
        return future

```

## High-Level Overview

This is a Python file located at `python/ccxt/async_support/base/ws/future.py`.

**Classes defined**: Future

**Functions defined**: callback, reject, race, resolve

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 35
- Comment lines: 6
- Blank lines: 6

### Main Components

**Classes** (1):
- `Future`

**Functions** (4):
- `callback()`
- `race()`
- `reject()`
- `resolve()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/async_support/base/ws/future.py
```

