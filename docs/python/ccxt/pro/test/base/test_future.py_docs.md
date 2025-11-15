# Documentation: python/ccxt/pro/test/base/test_future.py

## File Metadata

- **Path**: `python/ccxt/pro/test/base/test_future.py`
- **Size**: 6,707 bytes
- **Lines**: 195
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import asyncio
import os
import sys

# Assuming the structure of test_shared_methods based on common unittest methods

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))))
sys.path.append(root)

from ccxt import ExchangeClosedByUser
from ccxt.async_support.base.ws.future import Future

# Helper functions
async def resolve_later(future, result, delay):
    await asyncio.sleep(delay)
    future.resolve(result)

async def cancel_later(future, delay):
    await asyncio.sleep(delay)
    future.cancel()

async def reject_later(future, err, delay):
    await asyncio.sleep(delay)
    future.reject(err)

async def test_resolve_before():
    print("test_resolve")
    future = Future()
    expected_result = "test"
    future.resolve(expected_result)
    assert future.done(), "Future is not marked as done"
    assert future.result() == expected_result, f"Expected result '{expected_result}', got '{future.result()}'"

async def test_reject():
    print("test_reject")
    future = Future()
    test_exception = Exception("test error")
    future.reject(test_exception)
    assert future.done(), "Future is not marked as done"
    try:
        future.result()
        assert False, "Expected an exception but none was raised"
    except Exception as e:
        assert str(e) == "test error", f"Expected 'test error', got '{str(e)}'"

async def test_race_success_before():
    print("test_race_success")
    future1 = Future()
    future2 = Future()
    race_future = Future.race([future1, future2])
    future1.resolve("first")
    result = await race_future
    future2.cancel()
    assert result == "first", f"Expected 'first', got '{result}'"

async def test_race_success_after():
    print("test_race_success")
    future1 = Future()
    future2 = Future()
    race_future = Future.race([future1, future2])
    asyncio.create_task(resolve_later(future1, "first", 0.01))
    result = await race_future
    future2.cancel()
    assert result == "first", f"Expected 'first', got '{result}'"

async def test_race_return_first_exception():
    print("test_race_return_first_exception")
    future1 = Future()
    race_future = Future.race([future1])
    future1.reject(Exception("Error in future1"))
    try:
        await race_future
        assert False, "Expected an exception but none was raised"
    except Exception as e:
        assert str(e) == "Error in future1", f"Expected 'Error in future1', got '{str(e)}'"

async def test_await_canceled_future():
    print("test_await_canceled_future")
    future = Future()
    try:
        future.cancel()
        await future
        assert False, "Expected an exception but none was raised"
    except asyncio.CancelledError as e:
        assert isinstance(e, asyncio.CancelledError), "Expected asyncio.CancelledError"

async def test_cancel():
    print("test_cancel")
    future = Future()
    asyncio.create_task(cancel_later(future, 0.1))
    try:
        await future
        assert False, "Expected an exception but none was raised"
    except asyncio.CancelledError as e:
        assert isinstance(e, asyncio.CancelledError), "Expected asyncio.CancelledError"

async def test_race_cancel():
    print("test_race_cancel")
    try:
        future1 = Future()
        future2 = Future()
        race_future = Future.race([future1, future2])
        race_future.cancel()
        future1.resolve("success")
        await race_future
        assert False, "Expected a cancelledError"
    except asyncio.CancelledError:
        assert True

async def test_race_mixed_outcomes():
    print("test_race_mixed_outcome")
    future1 = Future()
    future2 = Future()
    race_future = Future.race([future1, future2])
    future1.resolve("first")
    task = asyncio.create_task(reject_later(future2, Exception("Error in future2"), 0.1))
    result = await race_future
    assert result == "first", f"Expected 'first', got '{result}'"
    task.cancel()
    future2.cancel()

async def test_race_with_wait_for_timeout():
    print("test_race_with_wait_for_timeout")
    future1 = Future()

    task = asyncio.create_task(resolve_later(future1, "completed first", 2))

    # Attempt to race the futures with a timeout shorter than their resolution time
    try:
        race_future = Future.race([future1])
        await asyncio.wait_for(race_future, timeout=1)  # Timeout is set deliberately short
        assert False, "Expected a timeout but race_future completed"
    except asyncio.TimeoutError:
        # Expected outcome, the race_future should not complete within the timeout
        assert True
    await task

async def test_race_with_wait_for_completion():
    print("test_race_with_wait_for_completion")
    future1 = Future()
    future2 = Future()

    task = asyncio.create_task(resolve_later(future1, "completed first", 0.1))

    # Race the futures with a timeout longer than necessary
    try:
        race_future = Future.race([future1, future2])
        result = await asyncio.wait_for(race_future, timeout=1)
        assert result == "completed first", f"Unexpected race result: {result}"
    except asyncio.TimeoutError:
        assert False, "Did not expect a timeout"
    await task

async def test_race_with_precompleted_future():
    print("test_race_with_precompleted_future")
    future1 = Future()
    future2 = Future()
    future1.resolve("immediate success")
    # Immediately resolved future before race call
    race_future = Future.race([future1, future2])
    result = await race_future
    assert result == "immediate success", "Race did not correctly prioritize already completed future."

async def test_closed_by_user():
    print("test_closed_by_user")
    future1 = Future()
    future2 = Future()
    race_future = Future.race([future1, future2])
    task1 = asyncio.create_task(reject_later(future1, ExchangeClosedByUser(), 0.1))
    task2 = asyncio.create_task(reject_later(future2, ExchangeClosedByUser(), 0.1))
    try:
        await race_future
        assert False, "Expected an ExchangeClosedByUser"
    except ExchangeClosedByUser:
        assert True
        assert task1.done()
        assert task2.done()
    except Exception as e:
        assert False, f"Received Exception {e}"

async def test_ws_future():
    await test_resolve_before()
    await test_reject()
    await test_race_success_before()
    await test_race_return_first_exception()
    await test_cancel()
    await test_await_canceled_future()
    await test_race_cancel()
    await test_race_mixed_outcomes()
    await test_race_with_wait_for_timeout()
    await test_race_with_wait_for_completion()
    await test_race_with_precompleted_future()
    await test_closed_by_user()


```

## High-Level Overview

This is a Python file located at `python/ccxt/pro/test/base/test_future.py`.

**Functions defined**: test_resolve_before, reject_later, test_race_success_before, test_race_return_first_exception, test_race_success_after, test_await_canceled_future, cancel_later, test_reject, test_cancel, resolve_later

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 195
- Code lines: 163
- Comment lines: 6
- Blank lines: 26

### Main Components

**Functions** (17):
- `cancel_later()`
- `reject_later()`
- `resolve_later()`
- `test_await_canceled_future()`
- `test_cancel()`
- `test_closed_by_user()`
- `test_race_cancel()`
- `test_race_mixed_outcomes()`
- `test_race_return_first_exception()`
- `test_race_success_after()`
- `test_race_success_before()`
- `test_race_with_precompleted_future()`
- `test_race_with_wait_for_completion()`
- `test_race_with_wait_for_timeout()`
- `test_reject()`
- `test_resolve_before()`
- `test_ws_future()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
pytest python/ccxt/pro/test/base/test_future.py
```

