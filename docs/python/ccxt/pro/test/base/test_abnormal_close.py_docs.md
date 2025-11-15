# Documentation: python/ccxt/pro/test/base/test_abnormal_close.py

## File Metadata

- **Path**: `python/ccxt/pro/test/base/test_abnormal_close.py`
- **Size**: 2,350 bytes
- **Lines**: 73
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import asyncio
import os
import sys


# ------------------------------------------------------------------------------

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))))
sys.path.append(root)

import ccxt.pro as ccxt
import logging
import psutil
import socket


KILL_AFTER = 20


async def tcp_kill_after(seconds):
    await asyncio.sleep(seconds)
    logging.debug("tcp_kill")
    current_process = psutil.Process(os.getpid())
    connections = current_process.net_connections(kind='tcp')
    for conn in connections:
        if conn.status == psutil.CONN_ESTABLISHED:
            try:
                sock = socket.fromfd(conn.fd, socket.AF_INET, socket.SOCK_STREAM)
                local_address = conn.laddr.ip
                local_port = conn.laddr.port
                sock.shutdown(socket.SHUT_RDWR)
                sock.close()
                logging.info(f"Connection closed: {local_address}:{local_port} -> {conn.raddr.ip}:{conn.raddr.port}")
            except Exception as e:
                logging.error(f"Error closing connection: {e}")


async def test_abnormal_close():
    print('test_abnormal_close')
    received_network_error = False
    ex = ccxt.binance({
        # 'verbose': True
    })
    ex.set_sandbox_mode(True)
    asyncio.create_task(tcp_kill_after(15))
    start_time = ex.seconds()
    while True:
        if ex.seconds() - start_time > KILL_AFTER:
            break
        try:
            logging.info("calling watch_trades")
            await ex.watch_trades('BTC/USDT:USDT')
            logging.info("watch_trades returned")
        except ccxt.NetworkError as e:
            logging.info(f"received network error: {e}")
            if not received_network_error:
                received_network_error = True
            else:
                break
        except Exception as e:
            logging.info(f"received unexpected exception: {e}")
    assert received_network_error, "Failed to receive network error"
    print("test_abnormal_close between watch calls")
    await ex.watch_trades('BTC/USDT:USDT')
    await tcp_kill_after(1)
    await asyncio.sleep(2)
    await ex.watch_trades('BTC/USDT:USDT')
    await ex.close()

if __name__ == '__main__':
    logging.basicConfig(level=logging.DEBUG)
    asyncio.run(test_abnormal_close())

```

## High-Level Overview

This is a Python file located at `python/ccxt/pro/test/base/test_abnormal_close.py`.

**Functions defined**: tcp_kill_after, test_abnormal_close

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 73
- Code lines: 59
- Comment lines: 2
- Blank lines: 12

### Main Components

**Functions** (2):
- `tcp_kill_after()`
- `test_abnormal_close()`

**Constants** (1):
- `KILL_AFTER`



## Usage Examples

### Main execution block:

```python
logging.basicConfig(level=logging.DEBUG)
    asyncio.run(test_abnormal_close())
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
pytest python/ccxt/pro/test/base/test_abnormal_close.py
```

