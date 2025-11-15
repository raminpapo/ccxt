# Documentation: wiki/examples/py/aiohttp-custom-session-connector.md

## File Metadata

- **Path**: `wiki/examples/py/aiohttp-custom-session-connector.md`
- **Size**: 594 bytes
- **Lines**: 31
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Aiohttp Custom Session Connector](./examples/py/)


 ```python
 # pip install aiohttp_socks

import asyncio
import ccxt.async_support as ccxt
import aiohttp
import aiohttp_socks

async def test():

    connector = aiohttp_socks.ProxyConnector.from_url('socks5://user:password@127.0.0.1:1080')
    session = aiohttp.ClientSession(connector=connector)

    exchange = ccxt.binance({
        'session': session,
        # ...
    })

    # ...

    await exchange.close()  # Close the exchange
    await session.close()  # don't forget to close the session

    # ...

asyncio.run(test())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/aiohttp-custom-session-connector.md`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 16
- Comment lines: 4
- Blank lines: 11

### Main Components

**Functions** (1):
- `test()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

