# Documentation: examples/js/delta-maintenance-margin-rate-max-leverage.js

## File Metadata

- **Path**: `examples/js/delta-maintenance-margin-rate-max-leverage.js`
- **Size**: 2,419 bytes
- **Lines**: 61
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js';

console.log ('CCXT Version:', ccxt.version);

function getMaxLeverage (market, positionSize) {
    /**
     * @description Equation taken from https://www.delta.exchange/contracts/
     * @param {object} market CCXT market
     * @param {float} positionSize The value of the position in quote currency
     * @returns The maximum leverage available for the market for the given position size
     */
    const info = market['info'];
    const maxLeverageNotional = Number (info['max_leverage_notional']);
    const initialMarginScalingFactor = Number (info['initial_margin_scaling_factor']);
    let initialMargin = Number (info['initial_margin']);

    if (positionSize <= maxLeverageNotional) {
        const initialMarginRatio = initialMargin / 100;
        return 1 / initialMarginRatio;
    } else {
        initialMargin = initialMargin + (initialMarginScalingFactor * (positionSize - maxLeverageNotional));
        const initialMarginRatio = initialMargin / 100;
        return 1 / initialMarginRatio;
    }
}

function getMaintenanceMarginRate (market, positionSize) {
    /**
     * @description Equation taken from https://www.delta.exchange/contracts/
     * @param {object} market CCXT market
     * @param {float} positionSize The value of the position in quote currency
     * @returns The maintenance margin rate as a percentage for the market with the given position size
     */
    const info = market['info'];
    const maxLeverageNotional = Number (info['max_leverage_notional']);
    const maintenanceMarginScalingFactor = Number (info['maintenance_margin_scaling_factor']);
    const maintenanceMargin = Number (info['maintenance_margin']);

    if (positionSize <= maxLeverageNotional) {
        return maintenanceMargin;
    } else {
        return maintenanceMargin + (maintenanceMarginScalingFactor * (positionSize - maxLeverageNotional));
    }
}

async function main () {

    const exchange = new ccxt.delta();
    await exchange.loadMarkets ();
    
    const symbol = 'ADA/USDT:USDT';
    const market = exchange.market (symbol);

    // Gets the maximum leverage and maintenance margin rate for a position worth 100,000 USDT on the ADA/USDT:USDT market
    const maxLeverage = getMaxLeverage(market, 100000);
    const maintenanceMarginRate = getMaintenanceMarginRate(market, 100000);
    console.log(maxLeverage, maintenanceMarginRate);
}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/delta-maintenance-margin-rate-max-leverage.js`.

**Functions defined**: main, getMaintenanceMarginRate, getMaxLeverage

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 49
- Comment lines: 13
- Blank lines: -1

### Main Components

**Functions** (3):
- `getMaintenanceMarginRate()`
- `getMaxLeverage()`
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/delta-maintenance-margin-rate-max-leverage.js
```

