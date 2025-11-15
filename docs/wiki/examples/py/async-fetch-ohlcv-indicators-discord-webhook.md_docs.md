# Documentation: wiki/examples/py/async-fetch-ohlcv-indicators-discord-webhook.md

## File Metadata

- **Path**: `wiki/examples/py/async-fetch-ohlcv-indicators-discord-webhook.md`
- **Size**: 2,302 bytes
- **Lines**: 62
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Fetch Ohlcv Indicators Discord Webhook](./examples/py/)


 ```python
 from asyncio import run, gather, ensure_future
import pandas_ta as ta
import pandas as pd
import ccxt.async_support as ccxt  # noqa: E402
print('CCXT Version:', ccxt.__version__)

async def send_discord_webhook_messsage(exchange, symbol, message):
    payload = {
        "username": "Kj Bot Top 10 Coins 15 Min TF",
        "content" : message
    }
    # change your webhook URL here
    url = 'https://discord.com/api/webhooks/xxxxxxxxxxxxxxxxxx/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
    method = 'POST'
    headers = {'Content-Type': 'application/json'}
    body = exchange.json(payload)
    try:
        await exchange.fetch(url, method, headers, body)
    except Exception as e:
        print(type(e).__name__, str(e))


async def run_ohlcv_loop(exchange, symbol, timeframe, limit):
    since = None
    while True:
        try:
            ohlcv = await exchange.fetch_ohlcv(symbol, timeframe, since, limit)
            if len(ohlcv):
                df = pd.DataFrame(ohlcv, columns=['time', 'open', 'high', 'low', 'close', 'volume'])
                rsi = df.ta.rsi()
                df = pd.concat([df,rsi], axis=1)
                last_row = df.iloc[-1]
                previous_row = df.iloc[-2]
                if last_row['RSI_14'] and previous_row['RSI_14']:
                    now = exchange.milliseconds()
                    iso8601 = exchange.iso8601(now)
                    print(iso8601, timeframe, symbol, '\tRSI_14 =', last_row['RSI_14'])
                    rsienterob = previous_row['RSI_14'] < 70 and last_row['RSI_14'] > 70
                    if rsienterob:
                        message =  iso8601 + ' ' + timeframe + ' ' + symbol + ' is entering overbought zone'
                        print(message)
                        ensure_future(send_discord_webhook_messsage(exchange, symbol, message))
        except Exception as e:
            print(type(e).__name__, str(e))


async def main():
    exchange = ccxt.binance()
    timeframe = '1m'
    limit = 50
    symbols = [ 'BTC/USDT', 'ETH/USDT' ]
    loops = [run_ohlcv_loop(exchange, symbol, timeframe, limit) for symbol in symbols]
    await gather(*loops)
    await exchange.close()


run(main()) 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-fetch-ohlcv-indicators-discord-webhook.md`.

**Functions defined**: main, send_discord_webhook_messsage, run_ohlcv_loop

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 62
- Code lines: 52
- Comment lines: 1
- Blank lines: 9

### Main Components

**Functions** (3):
- `main()`
- `run_ohlcv_loop()`
- `send_discord_webhook_messsage()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

