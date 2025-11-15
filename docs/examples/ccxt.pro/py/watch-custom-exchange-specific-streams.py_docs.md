# Documentation: examples/ccxt.pro/py/watch-custom-exchange-specific-streams.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/watch-custom-exchange-specific-streams.py`
- **Size**: 1,288 bytes
- **Lines**: 46
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import asyncio
import ccxt.pro


class MyBinance(ccxt.pro.binance):

    def handle_mini_ticker(self, client, message):
        market_id = self.safe_string_lower(message, 's')
        message_hash = market_id + '@miniTicker'
        client.resolve(message, message_hash)

    def handle_message(self, client, message):
        handlers = {
            '24hrMiniTicker': self.handle_mini_ticker,
            # add other custom handlers here
        }
        e = self.safe_string(message, 'e')
        method = self.safe_value(handlers, e)
        if method:
            return method(client, message)
        else:
            return super(MyBinance, self).handle_message(client, message)


async def main():
    exchange = MyBinance({
        'enableRateLimit': False,
        'options': {
            'defaultType': 'future'
        }
    })
    await exchange.load_markets()
    # exchange.verbose = True  # uncomment for debugging purposes
    market = exchange.market('BTC/USDT')
    message_hash = market['lowercaseId'] + '@miniTicker'
    while True:
        try:
            print(await exchange.watch_public(message_hash))
        except Exception as e:
            print(type(e).__name__, str(e))
    await exchange.close()


if __name__ == '__main__':
    asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/watch-custom-exchange-specific-streams.py`.

**Classes defined**: MyBinance

**Functions defined**: main, handle_mini_ticker, handle_message

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 35
- Comment lines: 2
- Blank lines: 9

### Main Components

**Classes** (1):
- `MyBinance`

**Functions** (3):
- `handle_message()`
- `handle_mini_ticker()`
- `main()`



## Usage Examples

### Main execution block:

```python
asyncio.run(main())
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/ccxt.pro/py/watch-custom-exchange-specific-streams.py
```

