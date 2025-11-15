# Documentation: examples/ccxt.pro/js/calculate-ohlcvs-from-trades.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/calculate-ohlcvs-from-trades.js`
- **Size**: 2,550 bytes
- **Lines**: 59
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../../ccxt');

console.log ('CCXT Version:', ccxt.version)


async function main() {
    let ohlcvs = {}
    const symbol = 'BTC/USDT'
     const exchange = new ccxt.pro.binance ({ 'newUpdates': true })
    await exchange.loadMarkets ()
    const market = exchange.market (symbol)
    const timeframe = '1m'
    const duration = exchange.parseTimeframe (timeframe) * 1000
    console.log ('Starting', exchange.id, symbol)
    while (true) {
        try {
            const trades = await exchange.watchTrades(symbol)
            for (const trade of trades) {
                const timestamp = parseInt(trade['timestamp'] / duration) * duration
                let candle = exchange.safe_value(ohlcvs, timestamp)
                if (candle) {
                    candle[2] = Math.max(trade['price'], candle[2])
                    candle[3] = Math.min(trade['price'], candle[3])
                    candle[4] = trade['price']
                    candle[5] = exchange.parseNumber(exchange.amountToPrecision(symbol, trade['amount'] + candle[5]))
                    candle[6] = exchange.parseNumber(exchange.costToPrecision(symbol, trade['cost'] + candle[6]))
                } else {
                    candle = [
                        timestamp,
                        trade['price'],
                        trade['price'],
                        trade['price'],
                        trade['price'],
                        exchange.parseNumber(exchange.amountToPrecision(symbol, trade['amount'])),
                        exchange.parseNumber(exchange.costToPrecision(symbol, trade['cost'])),
                    ]
                }
                ohlcvs[timestamp] = candle
            }
            console.log ('')
            console.log (exchange.iso8601 (exchange.milliseconds ()), '------------------------------------------------------')
            const values = Object.values (ohlcvs).slice (-1000)
            ohlcvs = exchange.indexBy (values, 0)
            console.log ('Datetime                ', 'Timestamp    ', ... [ 'Open', 'High', 'Low', 'Close', market['base'], market['quote'] ].map (x => x.toString ().padEnd (10, ' ')))
            for (let i = 0; i < values.length; i++) {
                const candle = values[i]
                console.log (exchange.iso8601 (candle[0]), ... candle.map (x => x.toString ().padEnd (10, ' ')))
            }

        } catch (e) {
            console.log (e.constructor.name, e.message)
        }
    }
    await exchange.close ()
}

main()
```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/calculate-ohlcvs-from-trades.js`.

**Functions defined**: main



## Detailed Walkthrough

### Code Structure

- Total lines: 59
- Code lines: 53
- Comment lines: 0
- Blank lines: 6

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/ccxt.pro/js/calculate-ohlcvs-from-trades.js
```

