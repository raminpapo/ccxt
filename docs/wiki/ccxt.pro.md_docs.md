# Documentation: wiki/ccxt.pro.md

## File Metadata

- **Path**: `wiki/ccxt.pro.md`
- **Size**: 3,356 bytes
- **Lines**: 45
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
# CCXT Pro

CCXT supports WebSockets (`Pro` part) for many exchanges.

- [User Manual](ccxt.pro.manual)
  - [Architecture Overview](ccxt.pro.manual#overview)
  - [Prerequisites](ccxt.pro.manual#prerequisites)
  - [Streaming Specifics](ccxt.pro.manual#streaming-specifics)
  - [Linking](ccxt.pro.manual#linking)
  - [Instantiation](ccxt.pro.manual#instantiation)
  - [Exchange Properties](ccxt.pro.manual#exchange-properties)
  - [Unified API](ccxt.pro.manual#unified-api)
    - [Public Methods](ccxt.pro.manual#public-methods)
      - [Market Data](ccxt.pro.manual#market-data)
        - [`watchOrderBook (symbol, limit, params)`](ccxt.pro.manual#watchOrderBook)
        - [`watchOrderBookForSymbols (symbols, limit, params)`](ccxt.pro.manual#watchOrderBookForSymbols)
        - [`watchTicker (symbol, params)`](ccxt.pro.manual#watchTicker)
        - [`watchTickers (symbols, params)`](ccxt.pro.manual#watchTickers)
        - [`watchOHLCV (symbol, timeframe, since, limit, params)`](ccxt.pro.manual#watchOHLCV)
        - [`watchOHLCVForSymbols (symbolsAndTimeframes, since, limit, params)`](ccxt.pro.manual#watchOHLCVForSymbols)
        - [`watchTrades (symbol, since, limit, params)`](ccxt.pro.manual#watchTrades)
        - [`watchTradesForSymbols (symbols, since, limit, params)`](ccxt.pro.manual#watchTradesForSymbols)
        - [`watchBidsAsks (symbols, params)`](ccxt.pro.manual#watchBidsAsks)
        - [`watchLiquidations (symbol, since, limit, params)`](ccxt.pro.manual#watchBidsAsks)
        - [`watchLiquidationsForSymbols (symbols, since, limit, params)`](ccxt.pro.manual#watchForSymbols)
    - [Private Methods](ccxt.pro.manual#private-methods)
      - [Authentication](ccxt.pro.manual#authentication)
      - [Trading](ccxt.pro.manual#trading)
        - [`watchBalance (params)`](ccxt.pro.manual#watchBalance)
        - [`watchOrders (symbol, since, limit, params)`](ccxt.pro.manual#watchOrders)
        - [`watchOrdersForSymbols (symbols, since, limit, params)`](ccxt.pro.manual#watchOrdersForSymbols)
        - [`watchPosition (symbol, since, limit, params)`](ccxt.pro.manual#watchPosition)
        - [`watchPositions (symbols, since, limit, params)`](ccxt.pro.manual#watchPositions)
        - [`watchMyTrades (symbol, since, limit, params)`](https://github.com/ccxt-dev/ccxt/wiki/ccxt.pro/Manual#watchMyTrades)
        - [`watchDepositsWithdrawals (code, limit, params)`](https://github.com/ccxt/ccxt/wiki/Manual#watchDepositsWithdrawals)
        - [`watchMyLiquidations (symbols, since, limit, params)`](https://github.com/ccxt/ccxt/wiki/Manual#watchMyLiquidations)
        - [`watchMyLiquidationsForSymbols (symbols, since, limit, params)`](https://github.com/ccxt/ccxt/wiki/Manual#watchMyLiquidationsForSymbols)
    - REST alternatives:
      In addition to above methods, some major exchanges also support websocket methods for REST methods, like `createOrderWs` (which has same signature as `createOrder`). You can find them in `exchange.has` dictionary.
  - [UnWatch](ccxt.pro.manual#unwatch) (for stopping **watch** methods).
- [Error Handling](ccxt.pro.manual#error-handling)
- [Troubleshooting](https://github.com/ccxt/ccxt/wiki/Manual#troubleshooting)
- [How To Submit An Issue](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md#how-to-submit-an-issue)
- [Usage Examples](https://github.com/ccxt/ccxt/tree/master/examples)

```

## High-Level Overview

This is a Markdown file located at `wiki/ccxt.pro.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 41
- Comment lines: 1
- Blank lines: 3

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

