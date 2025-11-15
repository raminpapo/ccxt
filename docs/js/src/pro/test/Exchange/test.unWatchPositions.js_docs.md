# Documentation: js/src/pro/test/Exchange/test.unWatchPositions.js

## File Metadata

- **Path**: `js/src/pro/test/Exchange/test.unWatchPositions.js`
- **Size**: 3,086 bytes
- **Lines**: 70
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
async function createOrderAfterDelay(exchange) {
    await exchange.sleep(3000);
    await exchange.createOrder('BTC/USDT:USDT', 'market', 'buy', 0.001);
}
async function testUnWatchPositions(exchange, skippedProperties, symbol) {
    const method = 'unWatchPositions';
    exchange.setSandboxMode(true);
    // First, we need to subscribe to positions to test the unsubscribe functionality
    let positionsSubscription = undefined;
    try {
        // First call uses snapshot
        positionsSubscription = await exchange.watchPositions();
        // trigger a position update
        exchange.spawn(createOrderAfterDelay, exchange);
        // Second call uses subscription
        positionsSubscription = await exchange.watchPositions();
    }
    catch (e) {
        if (!testSharedMethods.isTemporaryFailure(e)) {
            throw e;
        }
        // If we can't subscribe, we can't test unsubscribe, so skip this test
        return false;
    }
    // Verify that we have a subscription
    assert(Array.isArray(positionsSubscription), exchange.id + ' ' + method + ' requires a valid positions subscription to test unsubscribe');
    // Assert unWatchPositions for one symbol is not supported
    let errorResponse = undefined;
    try {
        errorResponse = await exchange.unWatchPositions([symbol]);
    }
    catch (e) {
        errorResponse = e;
    }
    assert(errorResponse !== undefined, exchange.id + ' ' + method + ' must throw an error when unwatching a specific symbol, returned ' + exchange.json(errorResponse));
    // Test unwatching all positions (without specific symbols)
    let responseAll = undefined;
    try {
        responseAll = await exchange.unWatchPositions();
    }
    catch (e) {
        if (!testSharedMethods.isTemporaryFailure(e)) {
            throw e;
        }
        throw e;
    }
    // Verify the response for unwatching all positions
    assert(responseAll !== undefined, exchange.id + ' ' + method + ' must return a response when unwatching all positions, returned ' + exchange.json(responseAll));
    // Test that we can resubscribe after unwatching (to ensure cleanup was proper)
    let resubscribeResponse = undefined;
    try {
        resubscribeResponse = await exchange.watchPositions();
        exchange.spawn(createOrderAfterDelay, exchange);
        resubscribeResponse = await exchange.watchPositions();
    }
    catch (e) {
        if (!testSharedMethods.isTemporaryFailure(e)) {
            throw e;
        }
        // If resubscription fails, it might indicate the unwatch didn't work properly
        throw new Error(exchange.id + ' ' + method + ' failed to resubscribe after unwatch, indicating potential cleanup issues');
    }
    // Verify resubscription works
    assert(Array.isArray(resubscribeResponse), exchange.id + ' ' + method + ' must allow resubscription after unwatch, returned ' + exchange.json(resubscribeResponse));
    return true;
}
export default testUnWatchPositions;

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/test/Exchange/test.unWatchPositions.js`.

**Functions defined**: createOrderAfterDelay, testUnWatchPositions

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 70
- Code lines: 57
- Comment lines: 12
- Blank lines: 1

### Main Components

**Functions** (2):
- `createOrderAfterDelay()`
- `testUnWatchPositions()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `assert` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/pro/test/Exchange/test.unWatchPositions.js
```

